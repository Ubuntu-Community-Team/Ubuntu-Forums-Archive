---
title: "Headphones on imac"
date: 2005-06-08
forum: Apple PPC Users
---

### Post by everettattebury on 2005-06-08
I am using Ubuntu Hoary 5.04 on a 600mhz summer2001 iMac.  

Following advice on other threads, I was able to get sound working pretty good through the internal speakers, even with sound from many applications at the same time.

Tonight I thought I'd try listening through my headphones, and I discovered that plugging them in does not stop sound coming through the internal speakers.

Have any of you been able to solve this problem?

---

### Post by DJ_Max on 2005-06-09
[QUOTE=everettattebury]I am using Ubuntu Hoary 5.04 on a 600mhz summer2001 iMac.  

Following advice on other threads, I was able to get sound working pretty good through the internal speakers, even with sound from many applications at the same time.

Tonight I thought I'd try listening through my headphones, and I discovered that plugging them in does not stop sound coming through the internal speakers.

Have any of you been able to solve this problem?[/QUOTE]
I in the same situation as well. I'll play around with Alsa & OSS a little bit.

---

### Post by chascon on 2005-06-10
[QUOTE=][/QUOTE]
 check out my HowTo at
[http://ubuntuppc.info/12.html](http://ubuntuppc.info/12.html)

================================
For all you Fudsters:
You think there is no apple cult?
[http://www.edbydesign.com/books/1886411832.html](http://www.edbydesign.com/books/1886411832.html)

You think apple doesn't hold back specs?
"There are several barriers to a Linux for Macintosh 68K port. The first of these is that Apple don't want other operating systems on their machines. Whereas you can learn almost all of the workings of a PC from books you will find almost nothing written on the Apple Macintosh. Sometimes the Macintosh specifications and tech notes fill in the blanks at other times its neccessary to apply a great deal of guesswork and experimentation to figure out the hardware."
[http://mac.linux-m68k.org/docs/macpaper.php](http://mac.linux-m68k.org/docs/macpaper.php)

You think there is no concerted effort to closing hardware?
"Every few years some large vendors collude to try to lock the free systems out of a
technology.  A decade ago it was ethernet.  This time it was wireless.
Next, it will be RAID."
[http://openbsd.md5.com.ar/pub/OpenBSD/3.7/ANNOUNCEMENT](http://openbsd.md5.com.ar/pub/OpenBSD/3.7/ANNOUNCEMENT)
[http://kerneltrap.org/node/5150](http://kerneltrap.org/node/5150)

You say apple doesn't use gnu software or uses very little of it?
"We would like to recognize some of the major contributors of code to Darwin ... The GNU Project"
[http://developer.apple.com/darwin/projects/darwin/contributors.html](http://developer.apple.com/darwin/projects/darwin/contributors.html)
[http://www.apple.com/opensource/](http://www.apple.com/opensource/)

---

### Post by everettattebury on 2005-06-10
[QUOTE=chascon]check out my HowTo at
[http://ubuntuppc.info/12.html](http://ubuntuppc.info/12.html)
[/QUOTE]

Thank you for the link.   :) 

I read this, it seems that this depends on having a USB headphone or converter device.  I was hoping to be able to use the headphone jacks on the front of my iMac.  I actually get sound through them, but it comes through the internal speakers as well, and my goal is to be able to listen to music, or play games with sound, without disturbing my spouse. ](*,)

I guess I will have to break down and buy the necessary hardware.

Edit:  I was unable to find the device that chascon mentions, but I found a device for $19.99 called the "Alpha Omega 5.1 Digital Sound USB Audio Controller" which looks like it will do the same thing.  I have ordered it and will post here on my (hopefully) success with it.

---

### Post by pvz on 2005-08-05
Did you solve your sound issue? I also have a  600mhz iMac, and after initially having the same problem as you, I got it working now. I run KDE on it, but I guess it will be the same with Gnome. When you install alsamixergui you can then mute the pc speaker by clicking on the green icons above pc speaker, so they turn white. Adapt the master volume to your liking. Now just plug in your headphones in the sidepanel audiojack instead of the frontpanel jacks, and you should be able to listen to music without disturbing others. You can always adjust the settings by runing alsamixergui from a console.

---

### Post by everettattebury on 2005-08-07
[QUOTE=pvz]Did you solve your sound issue? I also have a  600mhz iMac, and after initially having the same problem as you, I got it working now. I run KDE on it, but I guess it will be the same with Gnome. When you install alsamixergui you can then mute the pc speaker by clicking on the green icons above pc speaker, so they turn white. Adapt the master volume to your liking. Now just plug in your headphones in the sidepanel audiojack instead of the frontpanel jacks, and you should be able to listen to music without disturbing others. You can always adjust the settings by runing alsamixergui from a console.[/QUOTE]
 Thanks pvz, this does just what I need.

---

