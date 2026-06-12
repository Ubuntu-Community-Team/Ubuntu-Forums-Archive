---
title: "squid deny dstdomain not working on 6.06 LTS"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by ir_syam on 2007-12-05
i've installed ubuntu server 6.06 to make proxy server using squid. working but did not work with web site blocking using dstdomain. my script as below

http_access allow localhost
########################################################################################################

acl ncsa_users proxy_auth REQUIRED

acl ps_network src 172.17.128.0/255.255.240.0
acl business_hours_ps time 8:15-22:45
acl maks maxconn 2
[B]acl bad dstdomain "/etc/squid/squid-block"
acl blockfiles urlpath_regex "/etc/squid/filetypes"[/B]


http_access allow ncsa_users
[B]http_access deny bad
http_access deny blockfiles[/B]
http_access allow ps_network business_hours_ps
http_access deny maks

###########################################################################################################
# And finally deny all other access to this proxy

/etc/squid/squid-block file does contain :-
.youtube.com
.playboy.com

and blockfiles :-
.(exe)$
.(rmvb)$

whats wrong with my script, authentication working fine. can anybody helping me whats wrong with the script.

---

