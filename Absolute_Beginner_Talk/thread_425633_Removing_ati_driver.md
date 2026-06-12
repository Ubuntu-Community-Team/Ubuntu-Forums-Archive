---
title: "Removing ati driver"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-04-27
Pretty simple question really. I had a bash at installing the ati driver with envy, only to then read the sticky in this area about the bug in FF, and the way to do it like that.

When i rebooted, i just get a black screen. but, black is in the monitor is showing black [the backlights are on]. So, i want to remove the ati driver envy put on, and follow the howto in this forum.

What is the easiest way to do this in the shell? i have something for opensuse, but i really doubt it will work.

---

### Post by SuperAndy on 2007-04-27
if it helps, the code for opensuse is:

sudo rpm -e $(rpm -qa | grep fglrx)

[obviously added the sudo there]

---

### Post by SuperAndy on 2007-04-28
ah, please help.

i cant be arsed to reinstall ubuntu :P

---

### Post by Najand on 2007-04-28
OK, I try to help you... Paste the output of the following command here:
```
aptitude search fglrx
```

---

### Post by Martin on 2007-04-28
SuperAndy, If i understand correctly you just want to get back to your orig. x config. Try this in a terminal and choose ati when offered the chance "sudo dpkg-reconfigure -phigh xserver-xorg" then run startx and you should be back in business

---

### Post by SuperAndy on 2007-04-28
martin, i did what you said, chose ati, and i am posting this from linux (:D)

is the other driver still on here though? and if i try a different howto on how to do it, will it interfere?

and here is that output:

i   fglrx-amdcccle                  - Catalyst Control Center for the ATI graphi
p   fglrx-control                   - Control panel for the ATI graphics acceler
v   fglrx-driver                    -                                           
v   fglrx-driver-dev                -                                           
v   fglrx-kernel                    -                                           
i   fglrx-kernel-2.6.20-15-generic  - ATI binary kernel module for Linux 2.6.20-
i   fglrx-kernel-source             - Kernel module source for the ATI graphics 
i   xorg-driver-fglrx               - Video driver for the ATI graphics accelera
i   xorg-driver-fglrx-dev           - Video driver for the ATI graphics accelera

---

### Post by Martin on 2007-04-28
Hi, I guess you're asking if the fglrx driver is still available now that your'e using the std. ati driver. Yes it should be unless you used apt or whatever to get rid of it. It shouldn't intefere with anything though, because it is no longer referenced by your new xorg.conf file.

---

### Post by SuperAndy on 2007-04-28
awesome.

so, theoretically speaking, if i were to follow amother howto on how to install graphics drivers, it should work? i.e., all this messing around wont affect it?

---

### Post by Martin on 2007-04-28
Basicaly - you should be set.
Your sig: "1GB Crappy Memory" if that refers to the quality - fair enough - slow memory is crappy, if it refers to the qty and you are mainly using linux - save your money, most std linux distribs only make use a max of 1gb anyway.

---

### Post by SuperAndy on 2007-04-28
aye, its just generic ebuyer stuff.

i also use vista though :P but yea, i have a plan for my computer. and eventually i will get a little laptop, to use ubuntu on without windows.

but yea, cheers for the interest, and thanks for the help!

---

