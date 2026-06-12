---
title: "Where is the KPPP Dial-Up Software?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by JW of Denver on 2007-11-12
Purchased "The Official Ubuntu Book, 2nd ed" today (11/12/07) and installed 7.04 on my i386. Can not find the KPPP software. It gave me a message that my i386 is not supported. Moved hard drive over to my Pentium 4 and re-installed software. Still can not find KPPP software for my Zoom external modems (one on each computer). Do I have to download this software with my Windows Vista system and if so where do I go to get it?

---

### Post by Shazaam on 2007-11-12
Go to your panel (taskbar), open System>Administration>Synaptic Package Manager. KPPP will be listed there for installation.
BTW, gnome-ppp works the same. Use KPPP if you installed Kubuntu, gnome-ppp if you installed Ubuntu. Or either one, your choice.

---

### Post by Bartender on 2007-11-13
JW -
KPPP is a dialer that comes with the KDE desktop environment.  I believe it's included in Kubuntu.  I know it's in MEPIS and PCLOS and Mint Bianca.  You won't find it in Ubuntu.  If you can take the PC to some place that has a standard ethernet broadband connection you could download KPPP via Synaptic Package Manager.  Chances are good that the PC will connect if you can find broadband.  I've had good luck at a couple of different places.  Plug the ethernet cable in before starting the PC.

Duncan and I were just talking about KPPP the other day
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

Read the whole thing.  I'm afraid you're going to find your Zoom externals aren't supported.  What's the exact model on those Zooms?

You're in the same Catch-22 as most of us dial-up folks.  Someone replies saying "download this".  Hello, you can't get online to download anything.  That's why you're asking for help, right?

Follow Duncan's directions for pppconfig.  It's a basic and pretty foolproof dialer.    

Also take a look at my directions for downloading Gnome-PPP from a Windows PC.  It's just a front-end for wvdial, so Gnome-PPP doesn't solve anything if you have an unsupported modem or a crappy ISP.  It just makes things a little easier if all the stars lined up and you can go online.

Also try the wvdial instructions.  wvdial will try to find a modem.  If it detects the Zoom you might be in luck.

---

### Post by Bartender on 2007-11-14
If you have dial-up at home, but access to broadband somewhere else, (my situation) take a look at the last page of this thread.
[http://ubuntuforums.org/showthread.php?t=391956&highlight=dial-up&page=4](http://ubuntuforums.org/showthread.php?t=391956&highlight=dial-up&page=4)

Someone added his Kubuntu CD to the sources list, then installed KPPP right into his Ubuntu via Synaptic.  I'm going to try that as soon as I can download the latest Kubuntu .iso and burn a CD.

---

