---
title: "Is dialup any easier on newer versions of Ubuntu?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by sharong on 2008-01-26
I'm using Dapper on a laptop, and have had all kinds of trouble setting up a modem connection.  I eventually got it working, but then it broke again (my fault for messing around with settings).

I wondered whether there's any advantage in upgrading to a newer version of Ubuntu.  Is this going to be any easier to set up if I do that?  Or it is much the same in all of them?

Thanks!

---

### Post by Kubunteando on 2008-01-26
I would not say it is any easier.

It seems that in the coming version 8.04 the dialup is more integrated in the network settings. So it could be a bit easier.

I have used KPPP (and Kubuntu Gutsy) and I did not have problems with the dial up.
I did only have to tweak some settings so I got it working at speeds higher than 33Kbps.

---

### Post by sharong on 2008-01-27
OK, thanks!  I may upgrade anyway, but was just curious to know if it was going to make things easier.  Still, I got it working last time, so I'm sure I can do it again...

---

### Post by cebobbitt on 2008-01-27
I have found that dialup on Dapper was real easy. You can use gnome-ppp, pon poff, or the built in netwook-admin. Any thing past Dapper I have found wvdial works best. Good Luck

---

### Post by Cubby on 2008-01-27
I have an external modem for dial-up and run wvdial via the terminal.  Here's how to set it up:

[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

Just a note:  to first use wvdial, in terminal, I had to do as root:
```
wvdialconf
```\
if you do it as user, it won't properly create the file with your modem specs.

Then as root, edit the wvidal.conf file using a text editor as is suggested at the link.

Now to run wvdial, enter 'wvdial' in terminal. 

I've recently updated my computer and use a serial to usb converter for my external modem.  If you use KPPP witht this type of converter, make sure you select ttyUSB0 under modem and do not set the speed higher than 57600, or else it won't dial up.

---

