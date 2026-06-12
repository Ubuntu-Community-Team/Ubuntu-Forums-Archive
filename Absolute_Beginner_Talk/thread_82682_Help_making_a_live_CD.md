---
title: "Help making a live CD"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by Ski1215 on 2005-10-27
I've been trying to burn Ubuntu onto a CD so I can create a live CD just so I can fool around with it and see how I like it and see whats compatible and wether its worth my time. I just want to learn more about it basically. I'm burning Ubuntu as an ISO on a CD and then booting from the CD, but I still end up with windows somehow. I'm pretty sure I'm burning it correctly..:confused:

---

### Post by stuporglue on 2005-10-27
> I've been trying to burn Ubuntu onto a CD so I can create a live CD just so I can fool around with it and see how I like it and see whats compatible and wether its worth my time. I just want to learn more about it basically. I'm burning Ubuntu as an ISO on a CD and then booting from the CD, but I still end up with windows somehow. I'm pretty sure I'm burning it correctly..

So, your problem is actually getting Ubuntu installed? Or creating a bootable live CD? 

To boot from CD on a PC, you need to make sure your BIOS is set to boot from CD, and that you have a bootable CD. 

Do you know how to burn an iso as an image? When you put CD burned from ISO in a computer, you should see a whole bunch of files on the CD, not a single ISO file.

---

### Post by cjpkot on 2005-10-27
Goto your system menu bar.
select  administration, then select synaptic package manager.
select the K3B package and all the extras with it. auto select from menu
It will have a number required packages to run.
Apply and it will automatically down load.
Goto applications after it has successfully down loaded.
Run applications, enter K3B
I just finished asking question and got an answer.
This is if you are going to run linux as your operating system

---

### Post by Ski1215 on 2005-10-27
[QUOTE=stuporglue]So, your problem is actually getting Ubuntu installed? Or creating a bootable live CD? 

To boot from CD on a PC, you need to make sure your BIOS is set to boot from CD, and that you have a bootable CD. 

Do you know how to burn an iso as an image? When you put CD burned from ISO in a computer, you should see a whole bunch of files on the CD, not a single ISO file.[/QUOTE]


Thats how I burned it. Then when my computer is starting up I'm hitting F12, then selecting boot from CD/DVD drive

---

### Post by stuporglue on 2005-10-27
How old is the machine? Do you have multiple DVD/CD drives? Does doing the same thing with the Windows (or other known good Linux) CD boot from the CD drive? 

If you've still got Windows working, you could make a boot floppy with "Smart Boot Manager". It'll let you choose to boot from the CD. 

[http://btmgr.sourceforge.net/](http://btmgr.sourceforge.net/) (their page is kinda broken. Click the .html file you want to read. :-)

---

### Post by Ski1215 on 2005-10-27
Its a dell notebook, inspiron 1150 and its a year and a month old. Its only got one CD/DVD combo drive on it and it booted my windows CD from the CD drive because I reformatted my HD no more than a month ago. I can't make a bootable floppy because there is no 3.5 drive either. I'm not sure what I'm doing wrong still.

Edit.
I searched and read a few other threads from the past. Somone recommended a program called Deepburn which I installed. It has an option "Burn iso image" thats what I chose and burned Ubuntu on a CD as an iso. That much I'm posititive of. I hit f12 and selected boot from CD and still nothing.

---

### Post by Ski1215 on 2005-10-27
I changed the boot order so that my CD drive is first and its not working. The driver is installed correctly too, oh well. I odered some of the free CD's so I guess I'll just wait till they come in the mail...even though I'm very impatient and excited to try Ubuntu.

---

### Post by Mustard on 2005-10-27
In the meantime you could try doing an md5 checksum on the live CD ISO and confirm it is ok that way.  There are a number of md5 checkers available free online for windows.  The md5 hash should be available from the site you downloaded the ISO from.

Another way to check the disk might be to slip it into another computers CD drive and if it boots up on that one you could probably assume the live CD is ok, and the problem is with your hardware.

---

### Post by Ski1215 on 2005-10-27
Thats a good idea. It wont do any irreverable damage will it? I would have to use a freinds computer on my floor and I dont want to ruin anything on their HD or software.

---

### Post by Mustard on 2005-10-27
[QUOTE=Ski1215]Thats a good idea. It wont do any irreverable damage will it? I would have to use a freinds computer on my floor and I dont want to ruin anything on their HD or software.[/QUOTE]

A LIVE CD is designed to give people a preview of Ubuntu without them having to actually install the operating system, so no, it won't alter their system by booting up with a LIVE CD.

---

### Post by xmastree on 2005-10-27
[QUOTE=cjpkot]Goto your system menu bar.
select  administration, then select synaptic package manager.

<snip>

This is if you are going to run linux as your operating system[/QUOTE]I think you mean "This is if you are **already running** linux as your operating system"

He's obviously not, as he can't boot from his live CD...

Ski1215: take a look at [**this**]("http://www.xmastree.34sp.com/ubuntu/burn") and make 100% sure you're burning the disc correctly.

---

### Post by Mustard on 2005-10-27
xmastree, I can tell you that Ski1215 is up and running with Ubuntu now, from another thread.  He was using the Powerpc Live CD by mistake, instead of the x86 CD.  He's now downloaded Ubuntu and is running an Ubuntu system.

---

### Post by xmastree on 2005-10-27
Ah, ok. Thanks for letting me know. I suppose it would make a difference, having the wrong CD... :???:

---

### Post by Ski1215 on 2005-10-28
Xmas and everyone else thank you for your help. I figured my mistake out from another thread where I think i explained things differently. I tried it out for a while tonight and I really like it. I'm going to download the installer and make some room on my tiny HD (30g) for it. 

I have a few questions though. Is there an alternative to iTunes, or a way I can retrieve my music from windows via Ubuntu?

---

### Post by xmastree on 2005-10-28
[QUOTE=Ski1215]I have a few questions though. Is there an alternative to iTunes, or a way I can retrieve my music from windows via Ubuntu?[/QUOTE]Assuming the music is on the Windows disk, you can just mount that partition and play the files witn one of the many multimedia players around. Personally I like xmms, which is virtually identical to winamp (even uses winamp skins) but there are others. Rhythmbox, totem, beep, etc.

You'll need to install the multimedia codecs first though.
Read this:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)
It's for 5.04, but most of the information is relevant to 5.10, just don't blindly follow the 'extra repositories' section or you'll end up with the wrong ones.

---

