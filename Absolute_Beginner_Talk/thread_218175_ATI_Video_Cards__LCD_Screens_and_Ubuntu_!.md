---
title: "ATI Video Cards  LCD Screens and Ubuntu !"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by hundaco on 2006-07-18
I am brand new to Ubuntu (and Linux for that matter).  I have two machines, a Pentium II 800 with Nvidia 5200 video card and a Pentium 4, 3.4 with and ATI PCIE X700 video card.
The install on the P3 800 machine was a snap.  I only had to make minor changes to the "xorg.conf" file to get 1280X1024 at 75 Hz for my LG LCD screen.  I followed the Unofficial guide to Ubuntu, [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper), to add Nvidia driver.   I am so impressed with the ease at which it all happened .... I know if you are reading this I am preaching to the converted!! however, my computer is fun again.
The install on the P4 with ATI machine initially went very well, but when I tried to load the ATI driver ... I had a steep learning curve with the command line.   I didn't have to reinstall I just ran "dpkg-reconfigure xserver-xorg" and hey presto I got my desktop back.   But I still have a problem trying to get 1.\ ATI drivers to stick and 2.\The ATI monitor autoconfigure to recognise my LCD screen.   I end up with either high refresh frequencies which my monitor doesn't like or I get 1024x748 at 60 Hz which I don't like.
I would appreciate any help here, please.  Even a sample of what my xorg.conf file should look like with the ATI x700 and LCD screen.

Thankyou in anticipation

---

### Post by ovimunt on 2006-07-18
Hi, 

Check my reply on this thread:

[http://www.ubuntuforums.org/showthread.php?t=217812]("http://www.ubuntuforums.org/showthread.php?t=217812")

I hope it will help. In any case I would recommend installing the ATI proprietary drivers as described here (**Method 2**):

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

---

