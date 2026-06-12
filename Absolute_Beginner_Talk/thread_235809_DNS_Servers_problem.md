---
title: "DNS Servers problem"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by artifex0 on 2006-08-13
I've just installed Ubuntu on my Mac, but I'm having a problem accessing the internet- I can access pages by typing their IP into firefox's address bar, but urls and links to urls don't seem to work.  I tried entering some DNS servers into the Networking control panel, but whenever I close the window and re-open it, the addresses are gone- reverted to the default ip.

At one point, after adding a DNS server, then choosing 'Create Location' from the Networking window's drop down menu, the internet worked perfectly for about twenty seconds, then abruptly stopped.

Any help would be appreciated.

---

### Post by artifex0 on 2006-08-13
I tried entering the DNS servers directly into resolv.conf, but every ten seconds, the file is overwritten with the following:

```

search domain_not_set.invalid
nameserver 192.268.0.1

```

I'm using a PPPoE connection (SBC Global DSL)- In Mac OSX, I never had to enter DNS servers, so I'm guessing that SBC is sending that IP which is overwriting my resolv.conf file, and apparently, not working in Ubuntu.

I have a couple of correct SBC DNS servers which I'm pretty sure work- is there any way to prevent my ISP from overwriting my DNS settings?

---

### Post by splot on 2006-08-15
I don't have the answer, but I wanted to say that I have an very similar problem.  I have to reset the DNS entries every time I reboot, and then I have to do it at least twice before they "stick" and don't revert.

---

### Post by xen on 2006-08-15
Not entirely on-topic, but try the DNS servers over at [http://www.opendns.com/]("OpenDNS"). I have used them for a while and they are great!

---

