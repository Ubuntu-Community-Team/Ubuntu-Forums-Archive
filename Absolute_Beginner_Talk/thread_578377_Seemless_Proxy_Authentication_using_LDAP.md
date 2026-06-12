---
title: "Seemless Proxy Authentication using LDAP"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by antomac on 2007-10-17
Hey All, 
            Im a relativly new to ubuntu as I've only been using it for about 2 months now. So apologies if this seems like a n00b question.  :confused:

I have an ubuntu box up and running and i have apache 2.2.6 compiled, made and running on the box. I also have squid 2.6, complied, made and installed. 2 days ago thanks to these wonderful forms I've figured out how to get my squid proxy server to authenticate Via LDAP so when a user opens a web browser they have to type there LDAP logon details to use the interweb. 

I've been asked by the powers that be, can we now make the proxy server seemless. If a user opens a web browser it will still use their LDAP logon details to authentication but with no users intervention at all. IE. from the users perspective they open a web brower and vola there on the web. but in the background they go through the squid proxy with authenticates them against their LDAP details. 

I've tried using the old google machine the closest thing I've come up with was this: 

[http://www.novell.com/coolsolutions/feature/17777.html](http://www.novell.com/coolsolutions/feature/17777.html)

but it does really seem to make sense to me.

havent really come up with much sofar. I've also had a look on the forms here but couldnt find anything thusfar. 

I'd be really really greatful for any help 
Thanks a mill

---

### Post by xyrer on 2007-10-23
Could I ask where exactly did you get the info for making squid authenticate with ldap?
Thanks.

---

### Post by antomac on 2007-10-24
Sure thing i found some code in the forms (it should have been this one cant remember exactly but i added it to my squid.conf file and it works) 

my squid.conf file 

======================
authenticate_ttl 24 hour
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT

cache deny all  

auth_param basic program /usr/lib/squid/ldap_auth -b [enter path to LDAP here] -h [LDAP SERVER] -f (uid=%s)

#example: 
#auth_param basic program /usr/lib/squid/ldap_auth -b ou=Users,dc=myorg,dc=com  -h ldap01.myorg.com -f (uid=%s)


auth_param basic children 10
auth_param basic credentialsttl 24 hours
auth_param basic realm Web-Proxy
acl ldap_auth proxy_auth REQUIRED
http_access deny !ldap_auth

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny to_localhost
acl our_networks src 10.0.0.0/255.255.255.0
http_access allow our_networks
icp_access allow our_networks
http_port [IP address of PC running squid]:3128 transparent
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY

access_log /usr/local/squid/var/logs/access.log squid
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
cache_effective_user nobody
visible_hostname [IP Address of PC runinng SQUID]
coredump_dir /usr/local/squid/var/cache
====================================


hope that makes sense!! 

Entered the above restarted squid and now anytime a user opens a web browser it prompts them for their LDAP logon details which they have to enter. 

However im looking to make the whole operation seamless if possible!! 
its driving me crazy! might have to abandon SQUID altogether and look at alternatives like Kerberos or Apache.

---

### Post by xyrer on 2007-10-31
Hi, I tried it but somehow it doesn't work:
```

auth_param basic program /usr/lib/squid/ldap_auth -b cn=internet,ou=empleados,dc=proxy2 -h proxy2 -f (uid=%s)
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
#auth_param basic credentialsttl 2 hours
auth_param basic casesensitive off

acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 80 # https
acl SSL_ports port 563 # snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 80 # ftp
acl Safe_ports port 80 # https
acl Safe_ports port 110 # pop
acl Safe_ports port 25 # smtp
acl Safe_ports port # gopher 80
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl purge method PURGE
acl connect method CONNECT
acl work time 08:00-17:00
acl numeric_IPs urlpath_regex ^[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+
acl ldap_auth proxy_auth REQUIRED
acl all src 192.168.0.0/255.255.0.0

http_access deny connect numeric_IPs all
http_access allow ldap_auth
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
# Only allow purge requests from localhost
http_access allow localhost
http_access deny all
http_reply_access allow all

```

This is the relevant info on my squid.conf

my ldap server has dc=proxy2, under that is ou=empleados, and below is cn=internet, below there are the users, my test subject is cn=jhon smith, with login jsmith and "pass" as password.

When I put this squid.conf to work, it asks for login and password but jsmith doesn't work.

Any ideas on what could be happening, I'm new to ldap, never used it before.
Thanks.

---

### Post by antomac on 2007-11-06
i actually had the same problem for a while. once i enabled SQUID proxy to authenticate with LDAP no matter what details i entered i wouldn't accept any user details try the following suggestion below is what i did and it now works for me i couldnt tell you why: 

In your config file you have the line 

auth_param basic program /usr/lib/squid/ldap_auth -b cn=internet,ou=empleados,dc=proxy2 -h proxy2 -f (uid=%s)

change it to 

auth_param basic program /usr/lib/squid/ldap_auth -b ou=empleados,dc=proxy2 -h proxy2 -f (uid=%s) 

In other words take out the "cn=internet" bit 

i did this and it worked for me. if your still having trouble get back to me

---

### Post by antomac on 2007-11-06
Oh and just in case anyone else was wondering, I checked the squid-cache mailling list out,

==============
Unfortunately if you enable ProxyAuth_Required there is no transparent
proxy, well not that I have seen lately, the way to set up the
transparent proxy is to create an ACL for the network subnet and allow
the entire network, that is how I/we run our transparent proxies then
with SARG Reporting which will then report on the IP address and usage 

================

So it seems you cant enable seemless proxy authenication with squid at the moment  :(

---

### Post by xyrer on 2007-11-06
I seem to not get it, I have the feeling that is not the squid part but the ldap part what's failing, but anyway, it didn't work, I will keep studying about ldap and test again, I can connect to the ldap server and navigate it, browse it and all, I don't know if the -h in the squid config would be better with the ip or just the hostname, I'll test it out.
Thanks.

---

### Post by xyrer on 2007-12-26
I finally managed to do it, indeed it was the ldap part, all I needed was to make an organizational unit, a group, and then some users inside, it works great, i put this line:

```
auth_param basic program /usr/lib/squid/ldap_auth -b "dc=myserver" -f "uid=%s" -h localhost
```

And now I'm testing group policies, they work good too.

Thank you very much.

---

