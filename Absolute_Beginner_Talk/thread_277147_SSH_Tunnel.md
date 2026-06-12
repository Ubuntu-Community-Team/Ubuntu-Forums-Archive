---
title: "SSH Tunnel"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by dr_d on 2006-10-14
Hey there..

I would like to browse the web from uni, without being restricted by their filtering system. I think I've figured out what to do, but I'd like some feedback before I actually go do them.

>> set up squid proxy on my ubuntu server. pick a local port in the config file, say 8888

>> ssh to ubuntu server from uni. use ssh port forwarding.
ssh 1234:myaccount.no-ip.org:8888

so this should listen on port 1234 on my laptop and forward the data thru an ssh tunnel to port 8888 on my server..

>> set my browser to use localhost:1234 as a proxy



am i on the right track here? also one other thing. would it be worth while to use the proxy even when i'm at home. i've heard that squid has web-caching... so would this speed up my browsing by any noticable amount?

any advise much appreciated,
cheers!

---

### Post by dmizer on 2006-10-14
i assume port 22 is blocked on your uni network then?

if so, it might just be easier to configure your ssh server to listen on port 1234 rather than 22.

if you just want to browse, do this:
```
ssh -X username@myaccount.no-ip.org:1234
```
btw ... i've never switched ssh ports, so i'm not sure if the ":1234" command will work exactly or not.

the -X <--capital x ... tunnels the x server through ssh.  so now, once you're connected, all you have to do is type: firefox ... in the terminal window, and up pops firefox from your home laptop.

---

### Post by dr_d on 2006-10-14
Hey, thanks for replying.

No actually, port 22 is one of the few which is allowed out.

The problem is I'm not running linux on my laptop anymore, so X11 forwarding wont work.


Actually, I've thought about it, and I guess I'm not really doing this to get past filtering restrictions at uni... I think the only reason I'm doing it is because I want to do something cool with my new ubuntu server.. So i guess the only question is will a caching proxy really speed up my connection...

---

