---
title: "apt proxy setup"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by Brad wilkinson on 2005-08-22
ok, well I've read the howtos and the Debian manual and all sorts, but I've still got some questions.

1. on my apt-proxy "server" I've installed the apt-proxy package via synaptic. do I now need to edit any of the lines in apt-proxy-v2.conf? I was thinking this one might need uncommenting and changing to the address of my router, i.e.

> ;; Server IP to listen on
;address = 192.168.0.254

should be

> ;; Server IP to listen on
address = 192.168.1.254

2. on my "clients" i need to edit the sources.list file to add a proxy lookup, the howto shows this

> # apt-proxy entries for standard modules
deb [http://localhost:9999/ubuntu](http://localhost:9999/ubuntu) hoary main restricted universe multiverse
deb-src [http://localhost:9999/ubuntu](http://localhost:9999/ubuntu) hoary main restricted universe multiverse

but my server is not localhost, as the server is just 1 of 4 machines hanging from a broadband modem/router. So should I replace localhost with the IP of the machine that will act as the "server"? i.e.

> # apt-proxy entries for standard modules
deb [http://192.168.1.19:9999/ubuntu](http://192.168.1.19:9999/ubuntu) hoary main restricted universe multiverse
deb-src [http://192.168.1.19:9999/ubuntu](http://192.168.1.19:9999/ubuntu) hoary main restricted universe multiverse

where 198.168.1.19 is the stable IP of my "server"

hope this is clear enough. 

cheers,

Brad

---

