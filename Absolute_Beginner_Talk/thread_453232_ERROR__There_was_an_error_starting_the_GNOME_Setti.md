---
title: "ERROR:  There was an error starting the GNOME Settings Daemon."
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-24
I get this error when I try to log in to Feisty Ubuntu:

[B][INDENT]There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings 
may not work correctly.

The last error message was:

Did not receive a reply.  Possible causes include:  the remote
application did not send a reply, the message bus security
policy blocked the reply, the reply timeout expired, or the
network connection was broken.

GNOME will still try to restart the Settings Daemon next time
you log in.[/INDENT][/B]

I enter my login/password and after a few minutes, Ubuntu presents me with my GNOME desktop and the above error message.  The delay is frustrating.

I'm new to Linux -- how does one go about troubleshooting an issue like this?

Thanks

Carl

---

### Post by LollYouSuckZor on 2007-05-24
I get the same error. I'll be watching this thread :)

---

### Post by stalkingwolf on 2007-05-24
as do I, when running the live CD or trying to install.
I have gotten the same error on 3 different machines all pretty
much the same hardware,
1.2 - 1.5 Gig processors
256 Mb ram
20 - 40 Gb HDD.

I also have 2 laptops
1 compaq evo 410c
1.5 gig processor
512 Mg ram
30 Gb HDD

and a Tohhiba Tecra
1.5 gig processor
256 Mb ram
40Gb Hdd
on these fiesty install fine with no error.
FWIW  the first 3 , 2 have 17 " monitors , the third a 19".  The laptop displays are 12.5 and 14 respectively.

---

### Post by cwmoser on 2007-05-25
Thanks for the help.  I solved it by fixing the /etc/network/interfaces file.
I had comments for:
auto  lo
iface  lo  inet  loopback

and Gnome must have been trying to connect to something resulting in the white box and delay.

I also let the  Network-Manager applet control the network settings.

This occurred when I was trying to set up a VPN Client and either installed a package or modified a file that screwed up my Ubuntu.


Also, make sure and follow the hint to disable ipv6 to vastly improve Internet performance:

sudo  vi  /etc/modprobe.d/aliases

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

then reboot



Carl

---

