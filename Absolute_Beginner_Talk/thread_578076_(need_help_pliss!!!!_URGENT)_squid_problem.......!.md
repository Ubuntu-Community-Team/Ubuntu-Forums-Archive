---
title: "(need help pliss!!!! URGENT) squid problem.......!!!!"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by chaosky on 2007-10-16
hi all!! this is my first visit to ubuntuforum and i would like to ask a small questions :confused:
i have installed ubuntu 7.04 feisty fawn on my laptop, the reason i install ubuntu on my laptop is i want to install/setup a proxy server using squid.
i have installed squid by using = apt-get install squid ( i got squid 2.6 installed) when the last instalation there was some problem the squid fail to create cache, i think this is not a big problem :confused:
okay, after the installation is 99% complete i edit the squid.conf, here some squid.conf on my = 

http_port 10.10.1.1:8080 transparent (10.10.1.1 is my proxy ip)
visible_hostname ubuntu (ubuntu is proxy hostname)
cache_mgr ubuntu 
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
acl tes src 10.10.1.5/16 ----> the client subnet is 255.255.0.0
http_access allow tes
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all

OKAY the main problem is the client can browsing but the client must set the ip and port proxy in their browser :mad: when i want set the browser to direct connection the browser is block by the proxy :confused: as far as i know the configuration above are transparent right...!!!!
but when i disable " http_access deny all " everything is fine
- i dont set anything in iptables because i have a router installed, all the redirect thing is set in my router. so i dont need to redirect again in my proxy server right....?:confused::confused:

pliss help me :(:(
thx for advanced

---

