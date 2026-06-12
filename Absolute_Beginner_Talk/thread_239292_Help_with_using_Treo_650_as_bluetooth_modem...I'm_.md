---
title: "Help with using Treo 650 as bluetooth modem...I'm desperate!"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by crash331 on 2006-08-19
Ok, I am trying to use a Treo 650 with my bluetooth laptop running Ubuntu.  I want to use it as a GPRS modem to get on the internet.  I know the 650 supports it and everything because it worked with cingular.  I have read several guides and tried setting up a ton of stuff.  As far as I can tell, the phone is set up on rfcomm0.

When I try to run sdptool browse, it never picks up anything. It keeps saying connection reset by peer.  If I try hcitool scan, I can get the mac address but that's about it.  I have made the ppp files and chat scripts and everytime I try, it just says connection reset by peer.  The Treo is from Cingular, and you have to go into the Treo and flip a switch to turn the DUN profile on.  I have tried everything with the profile on and off.  I have tried the guide on this forum, and on the wiki.  I am at a loss....

Oh, and bluetooth is functioning.  I have gnome-obex-send working fine and can send MP3s to my phone.

---

### Post by crash331 on 2006-08-19
I am trying to follow the wiki at [http://www.ubuntu-in.org/wiki/GPRS_Howto](http://www.ubuntu-in.org/wiki/GPRS_Howto)


But when I have to type sudo hcitool cc MAC_ADDR the phone hangs for a while.  Eventually, it's responsive again and I try the hcitool auth line and the terminal just says connection times out.

---

### Post by crash331 on 2006-08-19
bump

---

### Post by byunique on 2007-06-04
I ran across the same "connection timed out problem"... but wasn't a deal killer...

anyway, here's my documentation on how I got it working:

[http://ubuntuforums.org/showthread.php?t=464613](http://ubuntuforums.org/showthread.php?t=464613)

---

