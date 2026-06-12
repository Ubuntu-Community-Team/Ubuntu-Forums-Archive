---
title: "RAM requirements"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Emily on 2005-08-04
I am getting a new computer and was hoping to use Linux on my laptop, which I will still be using. Someone pointed me to the Linux Distribution Chooser, which sent me here. However, browsing these forums, I've seen various discussions that make it sound like the amount of RAM I have makes my machine sort of borderline in regard to whether Ubuntu would work.

The laptop is a Sony Vaio PCG-SR17 from circa 2000. It has a Pentium III processor and a whopping 192MB of RAM, which can't be upgraded further (i.e., I am a cheapskate). It came with Windows ME, but a friend of mine upgraded it to Windows XP a while back. It is an ultralight (<3 lbs.) laptop so it has no internal drives (argh), only a CD-ROM drive that attaches via a PC card. I usually use the PC Card slot for a Linksys wireless card, though. I have a Knoppix Live CD and haven't been able to run it on this computer. I get some error message along the lines of "BIOS too old."  ](*,) 

I've been using Firefox and Thunderbird on it with great success, and I anticipate using this machine more or less exclusively for Web/Email/IM. I won't need Office or other Windows-only programs anymore. I'm basically looking for a system that would make my life easier by being simple, non-crashy, and hopefully faster than XP has been.

Would my system be better off with Damn Small Linux, Puppy Linux, or Feather Linux (all mentioned in another thread, to someone who had half as much RAM as I do)? They sound so basic.  :-? What about the Lightweight Desktop project, which I've seen mentioned elsewhere? I'd appreciate any advice. I really like the look of Ubuntu, but if it's not right, it's not right.

---

### Post by varunus on 2005-08-04
192...You might be able to run Ubuntu with GNOME.  I'd recommend, instead, using XFCE.  Its very very similar to GNOME, but takes up a lot less memory.  It has almost as many features too, and uses GTK2 to render just like GNOME, so the same themes work in both.  Some info at [http://www.xfce.org](http://www.xfce.org)

There's a post in the Hoary Tips and Tricks section of the forum that talks about how to install XFCE on Ubuntu without installing GNOME at all.

---

### Post by macgyver2 on 2005-08-04
Well, I have Ubuntu running (with Gnome) on my Fujitsu Lifebook P-2040...it's an ultralight, too.  I got it at the beginning of 2002, so it's slightly newer than yours but it still only has an 800 MHz Crusoe processor and 256 MB RAM.  I looked up the stats on your notebook and they said that you have a 700 MHz Pentium III, which, while technically "slower" than mine actually performs a bit better.

I have no problems with Ubuntu on my machine.  At times I have to wait a second for a menu to pop up and programs like firefox or thunderbird don't open instantaneously...but hey, it's an old computer and I'm patient enough not to mind.  I want to keep using Gnome for now, but if I were to remove Gnome and use XFCE or one of the *box-es the desktop would be a bit more responsive...

Anyway, I hope that helps you...unfortunately I know nothing of those other distros you mentioned so I can't comment on any comparisions or anything.

Oh, and have you checked into any BIOS updates to solve that error message?

---

### Post by poofyhairguy on 2005-08-04
You have enough RAM for Gnome. It won't run super fast (look into XFCE after you get comfortable), but it will run ok.

I would try our live cd....that a way to see what works.

Ubuntu's minimum is 128 mb. Any less than that and it won't work as well.

---

### Post by maruchan on 2005-08-04
Linux does a good job with what RAM is available to it, so 192 megs should do you just fine. I run Ubuntu on a 500 MHz Celeron with 192 megs of RAM, and while it's not as responsive as my other machine with 1.5 gigs of RAM, it's fully usable. Give it a try (preferably with the live CD first)!

---

### Post by Emily on 2005-08-04
Thank you all! This gives me a good place to start, especially since I'll have another working computer and can spend some time fiddling. Sounds like I should try the Live CD or a regular install first, and if that is sluggish, try XFCE.

As for the BIOS thing, I have to confess that I did not realize it could be changed! Usually I am less clueless--looks like they did an update [two years ago](http://esupport.sony.com/perl/swu-download.pl?mdl=PCGSR17&upd_id=978&os_id=4). D'oh. It is rather vexing that their instructions for doing the upgrade on a computer that does not have a floppy disk drive involve creating a floppy disk, but I guess that's a problem for another day.

---

### Post by Aksu on 2005-08-09
What happens, if I add some more memory to my machine (if there are slots available). Will Ubuntu recognize that after reboot automatically. I mean, is it an easy job to do?

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=Aksu]What happens, if I add some more memory to my machine (if there are slots available). Will Ubuntu recognize that after reboot automatically?[/QUOTE]

yes

---

