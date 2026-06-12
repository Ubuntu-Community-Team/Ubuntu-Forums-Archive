---
title: "Shorewall dedicated firewall/router  - i think this may be a dnat question"
date: 2013-07-05
forum: Any Other OS
---

### Post by held7over on 2013-07-05
I've been looking for examples of how to do this, but everything I have found skips right over it like I should already know how to do it. 

It seems I do not understand how to construct a (dnat?) statement (I am assuming it would be in the /etc/shorewall/rules and/or the masq file or both) that will allow communications from different subnets being handled by my firewall/router to the internet or communications bewteen the two different lan subnet lans being handled by the shorewalled pc. 

My /etc/shorewall directory contains these active modules:  
interfaces  Makefile  masq  modules  params  policy  routestopped  rules  shorewall.conf  zones

Physical Description:  I have three physical ethernet cards installed in a old pc, with each ethernet card having a different subnet address of xxx.xxx.xxx.254 except for the eth0 card which is facing the internet whose IP is control by dhcp. My dmz's server computer is directly attached via crossover cable to one of the firewall computer's ethernet interface cards. I have moved my Linksys Router to now act as a switch between my shorewall firewall/router pc and my loc network of personal computers.

From what I have gleaned from reading different shorewall howto's, my files look like this:


_ZONES FILE_  | _THE INTERFACES FILE_                                           | _resulting subnets_
fw      firewall          |         
net     ipv4             |  net     eth0    detect   dhcp,tcpflags,routefilter,logmartians  | 192.168.1.x (assigned via DSL Modem)
loc     ipv4              |   loc      eth1   detect   tcpflags,routefilter,logmartians         | 192.168.2.x
dmz   ipv4              |   dmz    eth2   detect   tcpflags,routefilter,logmartians         | 10.9.5.x

          _POLICY FILE_                         |         _MASQ FILE_
net             all             DROP            info    |  eth0               10.0.0.0/8,\
dmz            all             REJECT                  |                        169.254.0.0/16,\
loc              all             REJECT                  |                        172.16.0.0/12,\
fw               all             ACCEPT                 |                        192.168.0.0/16

My RULES file has changed a lot as I've tried different things--


What should my RULES (and MASQ?) file say, in order to allow my loc computers attached to my firewall's interface via the Linksys switch to:
(A) access the internet?
(B) allow ssh access to my dmz system?
(C) and also allow my dmz server to serve pages to my loc computers so I can test my work on the server?

Thanks!

---

### Post by held7over on 2013-07-07
Never mind. Sorry about the overcomplicated post.

---

### Post by held7over on 2013-07-07
Never mind. Sorry about the overcomplicated post.

---

