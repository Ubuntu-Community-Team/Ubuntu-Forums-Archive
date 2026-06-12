---
title: "wierd SSH problems"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Ronfar on 2007-08-06
I installed a OpenSSH server on a Desktop pc at my house to connect to when I am at unknown wireless hotspots, Everything went fine untill I logged on and rebooted the server from my laptop now when I try to connect I get 

ssh: connect to host ********* port 22: Connection refused

However I never set it up to run on port 22 I set it up to run on port 112 right off the bat and I checked the configuration file and it still says it's supposed to run on this port.

I Nmaped the server and I got this:


PORT    STATE SERVICE
112/tcp open  mcidas

What is mcidas?

Is there some kind of problem with me running it on this port? I don't see why that would be a problem.

---

### Post by p_quarles on 2007-08-07
The only mcidas that I could find that related to internet services is this:
[http://www.ssec.wisc.edu/mcidas/](http://www.ssec.wisc.edu/mcidas/)

This could mean that nmap simply relates that port to this service, or that someone hacked your system. I would check all of your logs for any signs of suspicious connections, particularly around the time this started.

That's a precaution, though (a good one, but just a precaution). Another possibility is that for some reason your ssh server didn't restart when you rebooted the computer. If you haven't already, try this:
```
sudo /etc/init.d/ssh restart
```
Yet another possibility is that the ssh client on your laptop got screwed up when it disconnected during the reboot. Have you looked at the config files for it?

---

### Post by Ronfar on 2007-08-07
Yeah, that ended up being the problem.. For some reason it set the host port on the client side to only connect to 22.. Don't know why it was commented out before, oh well all problems are fixed thanks for taking the time to help.

---

