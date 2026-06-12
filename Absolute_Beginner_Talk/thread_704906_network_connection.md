---
title: "network connection"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by va7ani on 2008-02-22
just finished upgrading to gutsy.
Had a connection to the internet, checked my e-mail etc.
Then I rebooted into Windows XP, did some work and returned to Ubuntu.
Now I don't have a connection to the internet.
I'm typing this from a live CD of Ubuntu and it seems to work ok, also Windows connects to the internet ok.
I did a ifconfig and it looked ok
I did a ifconfig eth0 up and that seemed ok
Tried to ping my router and I got the message "network not available"
Anyone have a quick idea.

Walter

---

### Post by Presto123 on 2008-02-22
This is just a basic possibility, but, fully shut down your computer after coming out of Windows. As of right now you can shut down the computer, wait a bit, and restart and see if that gets any results.

The card may not have been released by Windows. I had the same issue, but with a sound card.

---

### Post by kool_kat_os on 2008-02-22
maybe the driver is not installed properly...or it is not compatible with a piece of software that you may have installed(if any) 
thats all i could think of.

---

### Post by va7ani on 2008-02-22
Nope. Rebooting didn't help. I guess I'll have to download an iso and re-install from a CD

Walter

---

### Post by superprash2003 on 2008-02-22
were you getting an ip when you typed ifconfig???cause if you were then you should have been able to ping to your router!!... check the eth0 properties.. and change it to DHCP if not so!!

---

### Post by va7ani on 2008-02-23
I'm back.
Went into System > Administration > Network.
Found my connection was set to "Roaming"
Selected "Properties" and found it set to "Static"
Changed it to "Automatic" and exited.
My connection to the internet is now restored.

Simple fix.

Now I have to think what I did to cause my network card to be set to a static IP when I rebooted from Ubuntu Gutsy  into WindowsXP and then back into Gutsy.. I don't remember messing with any network connections.

Walter

---

