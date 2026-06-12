---
title: "no network connection"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by torrey881 on 2007-10-30
hello there,

Brand new to Ubuntu. I seem unable to obtain a wired internet  connection on my laptop. It is a used laptop that I just installed Ubuntu on after installing a new hardrive this evening. The laptop is a compact presario 700 that I inherited because the former owner decided not to spring for a hardrive. I have an extensive local area network in good working order supporting a half dozen other machines. Having tried to remedy the issue with the network features in Ubuntu I am left wondering if perhaps the problem is a hardware one concerning the Ethernet connection itself.  Is there any item in Ubuntu that corresponds to  Windows' control panel that would allow me to see if the NIC is in good working order?


Thanks for any help or advice you could give a newbie!

---

### Post by gate on 2007-10-30
There are a few things you can look at, first there is the hardware manager in the system->administration menu. Make sure the information is what it should be.

  Second, open a terminal and type ifconfig and look at the output for eth0 or eth1. should be things like its MAC address, etc.

---

### Post by torrey881 on 2007-10-31
> **gate said:**
> There are a few things you can look at, first there is the hardware manager in the system->administration menu. Make sure the information is what it should be.

  Second, open a terminal and type ifconfig and look at the output for eth0 or eth1. should be things like its MAC address, etc.

I looked through the sytem administration menu but did not find a "hardware manager" as such. Al I found were items such as keying manager, language support, login window, network etc.

Secondly I did open a terminal and typed in ipconfig  and was most disappointed to have the machine return me the following---------bash: ipconfig: command not found.

Any suggestions as to what I should try next....thank you!

---

### Post by torrey881 on 2007-10-31
I'm beginning to think it is a hardware issue....there is no green light on my 24 port switch to show that my laptop is making a physical connection...i've tried switching cables, ports etc. ...I may try using a usb to ethernet gender changer next.

---

### Post by torrey881 on 2007-10-31
PROBLEM SOLVED:):):):)
I used a gender changer to allow my ethernet  wire to go through a usb port and instant connectivity! Therefore either my onboard ethernet is no good or for some unlikely reason it's not recognized by Ubuntu. I'm suspecting the first and not the latter.

Thanks for the replies....now I can get onto asking more newbie questions LOL

---

### Post by dwhitney67 on 2007-10-31
Just so you know, the proper command under Unix/Linux for viewing ethernet and loopback devices is *ifconfig*, not *ipconfig*.  The latter is the M$ version.

If it is not in your path, ifconfig resides in the /sbin directory.

You can determine if you system "sees" your network device by running this command:

[FONT="Courier New"]$ lspci | grep -i network[/FONT]

---

