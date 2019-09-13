# Start Apache service with updated certificate

Start the Apache service now that the certificates used comply with the
system-wide crypto policy.  Now that the service complies with the policy,
it should start without further issue.

`systemctl restart httpd.service`{{execute T1}}

You can verify the Apache service is now running again.   

`systemctl status httpd.service --no-pager`{{execute T1}}

<pre class="file">
<< OUTPUT ABRIDGED >>

Active: active (running) since Wed 2019-07-17 09:54:40 EDT; 2s ago

<< OUTPUT ABRIDGED >>
</pre>

Now that the service is running and certificates used comply with the FUTURE
system-wide cryptographic policy, connect to the Apache service and validate 
that the new certificate is being offered to client browsers.   

`openssl s_client -connect localhost:443 </dev/null 2>/dev/null | grep '^Server public key'`{{execute T1}}

<pre class="file">
Server public key is 3072 bit
</pre>
