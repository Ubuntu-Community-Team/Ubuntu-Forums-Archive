---
title: "G4 is getting dated, dual booting etc etc"
date: 2007-09-29
forum: Apple PPC Users
---

### Post by cysquatch on 2007-09-29
Hello everyone. First post, long time infrequent user. Okay, here's the story thus far...

I took a dive into linux about 6 years ago, dabbling between slackware, debian and ubuntu since. In some cases completely switched until I needed something in Adobe Illustrator or Photoshop.
About two years ago I purchased a PPC G4 PowerMac from a good friend for a very good price. I had just gotten back into graphic design and thought this would be very helpful with my work. Since then i traded up for another g4, this time a dual 867 MDD running os 10.4 with some CS2 apps and whatnot. Right now I have to say this machine does everything I would want to do on a computer. But I do miss Linux, Ubuntu especially. It flew on my AMD 2600+ PC (that now belongs to my girlfriend and her daughter), and now with OS 10.5 coming I'm starting to realize the age of my Mac.

At first I thought about trying to save my pennies and get a MacbookPro...until I saw the pricetag. Then I thought maybe a new iMac...until I saw the pricetag. Then I checked out the Sonnet dual 1.8 processor upgrade...the price is right, and I could get a few more years out of this system. Unless Steve pulls the usual lock-in B.S. and completely excludes PPC processors in the next couple years.

For now, I am thinking of getting the processor upgrade (dual 1.8's) and just running whatever will work down the road in two or three years time. Mac OS or Linux ( if linux ppc even still has a pulse by then).

So, my first question: Ubuntu ppc as a desktop system. Anything missing from what I might find for x86? I know there is no driver for the nvidia card on this thing, but I guess I have to deal with that.

My second question: Am I just paranoid about my g4 being out dated? We have a iMac g4 running os 10.2 that still works as your typical net-surfing music-playing desktop.

All in all I really would like to take a drive with a dual booted OS10.x/Linux setup. Any gotcha's or experiences any of you would like to share?

---

### Post by Auria on 2007-09-29
> **cysquatch said:**
> 
So, my first question: Ubuntu ppc as a desktop system. Anything missing from what I might find for x86? I know there is no driver for the nvidia card on this thing, but I guess I have to deal with that.

what comes to my mind:
- no adobe flash. there's Gnash but if you need reliable flash it probably won't be sufficient
- some packages/apps are only provided for x86 but you can often build from source
- forget Wine
- no Sun Java - there's GCJ and IBM's VM wich do a correct job i believe (never tried)
- 3D drivers are not very reliable
apart from that, it works very well on my computer. Of course there's a little more hardware incompatibilities than on OS X but for me there was not problem.

> **cysquatch said:**
> 
My second question: Am I just paranoid about my g4 being out dated? We have a iMac g4 running os 10.2 that still works as your typical net-surfing music-playing desktop.


I think it depends on what you want to do with it. If it works for what you do daily, no it's not :D When it's not enough for you, i think you'll notice.

> **cysquatch said:**
> 
All in all I really would like to take a drive with a dual booted OS10.x/Linux setup. Any gotcha's or experiences any of you would like to share?

Dual-booting works very well here and Ubuntu works very well. You just need to back-up important data first as partitionning is not the safest operation to do

---

### Post by cheezle on 2007-09-30
Also, on your machine, you could use Mac-on-Linux, which lets you run your mac partition within ubuntu.  It's supposedly not emulated so it's pretty fast.  Here's the site:  [http://mac-on-linux.sourceforge.net/news.php](http://mac-on-linux.sourceforge.net/news.php)

I really wish they'd have this working for G5's...  Hopefully it's in developement.

---

### Post by stmiller on 2007-09-30
Yeah I vote for going all Ubuntu, then creating a mac-on-linux VM of OS X inside Ubuntu for anything you may need. No dual booting needed, this way.

Here's a quick guide to make a disc image, and install OS X:

[http://mac-on-linux.sourceforge.net/wiki/index.php/InstallingMacOSX](http://mac-on-linux.sourceforge.net/wiki/index.php/InstallingMacOSX)

So you can make an expandable disk image. And to get rid of it, just delete the image. The speed is native to your CPU as it is true virtulization. But there is NO virtualization of the graphics, if that matters for your work. It basically uses a generic OS X video driver.

You'll want to get the latest MOL from SVN, and disregard any now out of date instructions you may see on how to install and configure MOL, and just follow the SVN readme.

---

### Post by cheezle on 2007-09-30
> **stmiller said:**
> Yeah I vote for going all Ubuntu, then creating a mac-on-linux VM of OS X inside Ubuntu for anything you may need. No dual booting needed, this way.

Here's a quick guide to make a disc image, and install OS X:

[http://mac-on-linux.sourceforge.net/wiki/index.php/InstallingMacOSX](http://mac-on-linux.sourceforge.net/wiki/index.php/InstallingMacOSX)

So you can make an expandable disk image. And to get rid of it, just delete the image. The speed is native to your CPU as it is true virtulization. But there is NO virtualization of the graphics, if that matters for your work. It basically uses a generic OS X video driver.

You'll want to get the latest MOL from SVN, and disregard any now out of date instructions you may see on how to install and configure MOL, and just follow the SVN readme.

Oh, see, I thought MOL was for using your mac partition within linux...

*edit*

Yeah, it says this in the PowerPCFAQ:

"Mac on Linux (sudo apt-get install mol) will let you boot up the OS X partition of a dual boot system, inside Linux. It is not software-emulated, so the actual speed is very fast. MOL currently only works on pre-G5 processors. It has not been ported to work on G5 processors yet, but a proper ppc64 port may be in the works."

---

### Post by stmiller on 2007-10-01
Ah thanks. Let me edit that...

---

