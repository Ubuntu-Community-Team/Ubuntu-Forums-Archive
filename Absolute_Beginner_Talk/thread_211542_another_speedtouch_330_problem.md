---
title: "another speedtouch 330 problem"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by rowlie on 2006-07-08
I am using this instruction after many failures >[http://nyati-buffaloblog.blogspot.com/2006/04/ubuntu-speedtouch-howto.html](http://nyati-buffaloblog.blogspot.com/2006/04/ubuntu-speedtouch-howto.html) and all is fine until I get here:
CODE TO TYPE:
[COLOR="Red"]sudo cp /your/path/to/speedtch.txt /etc/hotplug/usb/speedtch [/COLOR](/your/path/to must be replaced with the location of the speedtch.txt file)

(Now we are going to turn this script into an executable file... etc etc.)




and I get this reply:

"rollo@rollo-laptop:~$ sudo cp /home/rollo/speedtch.txt /etc/hotplug/usb/speedtch
cp: cannot create regular file `/etc/hotplug/usb/speedtch': No such file or directory
rollo@rollo-laptop:~$"

The speedtch.txt is as large as life in my home folder. So Im doing something wrong.  I is the method that seems to be going well so reluctant to stop and try the others again,-unles someone knows different. Grateful for help.I have tried to get connected for weeks continually .

---

### Post by keith whitehouse on 2006-07-08
hi rowlie,

if you go to the top right corner of this page there is a search box, just type in Speedtouch and you will find lots of posts about the Speedtouch modem. Just have a read through them and see if there is an answer that you can follow.

I had this modem and followed a guide that I found at

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

best regards keith

---

### Post by rowlie on 2006-07-08
Thanks Keith. Here I am duly connected to 't internet with Ubuntu! I used the link. In case others have password probs as I did  with tesco.net I used my "username@adsl.tesco.net" and my password  for that connection. Not getting that right was probably the real source of  all probs.
I can't see me using Microsoft very much now.ACE!!!!!

---

### Post by Jareth on 2006-08-27
Hi rowlie,
I'm having the exact same problem as you said at the top of this thread, can you tell me what you did to get around it?

I was thinkin of getting rid of the old speedtouch 330 and getting a netgear thingy with an ethernet connector, but if you can help you might save me £45!

Cheers!

---

### Post by Jareth on 2006-08-27
S'alright Rowlie, got it fixed.

---

### Post by ishaqzacf on 2007-05-19
> **Jareth said:**
> S'alright Rowlie, got it fixed.

Dear Jareth, I am happy you fixed your problem, but I did not know how? I am facing the same problem and will be great full if you help me .
Thanx

---

### Post by laidback on 2007-05-19
I dumped my speedtouch 330 for an eTEC router/modem that cost me about £25, it's sooooo much better. I wouldn't go back now. Well worth the expense even if you have got your speedtouch working.

---

### Post by StevenHarper on 2007-05-20
I have made a Debian Package to manage USB ADSL Modems and there Configuration

I Support Speedtouch USB 330 Modems

My Page it at

[https://launchpad.net/usb-adsl-modem-manager]("https://launchpad.net/usb-adsl-modem-manager")

You can download the package at [http://www.squeezedonkey.com/svn/linux/trunk/releases/]("http://www.squeezedonkey.com/svn/linux/trunk/releases/")

And read about it at
[http://www.squeezedonkey.com/wiki/li...itle=Main_Page]("http://www.squeezedonkey.com/wiki/li...itle=Main_Page")

Hope it makes your life easier

Steve

---

