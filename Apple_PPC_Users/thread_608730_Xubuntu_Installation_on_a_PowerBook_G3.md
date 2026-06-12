---
title: "Xubuntu Installation on a PowerBook G3"
date: 2007-11-10
forum: Apple PPC Users
---

### Post by Shrooms on 2007-11-10
Hello! :-D

I'm new here in this Forum, and right at the start I have a Question, or a Problem, for what I search an answer. By the way: it's not the first contact with Linux :)

So, I have got a PowerBook G3 Lombard (**New World Macintosh**, see for Specifications below, got it from uncle without OS X, after HD crashed), and I want to install Xubuntu (7.10 Gutsy Gibbon, Alternate PowerPC CD) on it. The PowerBook boots from the Installation CD, loads the Installation Program, but I just come to the Hardware, more precisely CD Drive, Detection. That's the point, where the road ends (I hope it is not really that way because others already did that).

He does not recognize the Macintosh PowerBook G3 Series 2x DVD-ROM Module (Model Number: M5505). So he cannot access the files that should be copied to the HD. What now?
I can load a driver from floppy, but the bad thing is, that I don't have a floppy drive in there. So I choose "No".
Now, he offers me the possibility to type in a CD-ROM-Module and Device manually. I choose Yes. Then I can 
select one module that is needed for CD Access, there are "none" and "cdrom". Then I choose cdrom, and I have to enter a Devicefile ( I hope it is correctly translated, I'm not a native speaker of english) for the access. Default is "/dev/cdrom". With Alt+F2 I can open a second console to list the avaible devices in "/dev". But there are so many with cryptic filenames... I already tried some. And to this, I always found answers in the internet, until now.

So what do I need (to do)?

My PowerBook Specifications:
[LIST]
[*]400MHz PowerPC
[*]128MB RAM
[*]About 10GB Hard Disk
[*]8MB Video RAM
[*]1MB Cache
[*]2x DVD Drive
[/LIST]

Pleeeease help me, I really want to get Linux running on that...

---

### Post by Shrooms on 2007-11-11
No one an idea or hint or whatever? :(

What is with the others, who had an old world Mac oder general a PowerBook G3, did it work there with the Drive? Which one had those? Is it the same interface (SCSI, or what it is)? Would it be possible, if I get an other drive, and try it with that one?

---

### Post by Shrooms on 2007-11-11
If there's no solution until next weekend, I'll sell that on eBay... -.-

---

### Post by flickerfly on 2007-11-29
Did you ever come up with a solution to this? If we could find the proper driver, you could use a USB key to get it into place.

---

### Post by khelben1979 on 2007-11-30
I myself is a owner of a Powerbook G3 Lombard (model from 1999) and I'm running Debian Etch on it and it works perfectly.

Did you get it working?

---

### Post by flickerfly on 2007-11-30
I haven't but maybe Debian Etch would be a good option. Any recommendations as far as wireless cards? I have an 18 month old so keeping cables off the floor is a good idea. I run the power cord under the couch to the outlet behind the couch to keep her from messing with it. :-) Having a network cable in the mix would further risk yanking and general distruction.

---

### Post by newbiexubunt on 2007-12-03
You're having the exact (well, maybe not exact) same problem as me.  I have a Lombard Mac Powerbook PPC (1999) and am doing the exact same thing.  Any ideas?:)

---

### Post by flickerfly on 2007-12-04
I'm thinking that the Lombard just isn't supported on the newer versions of Ubuntu. I had a similar problem with Gentoo a couple years ago when they forgot to include the CD driver in one version of the install CD and I had to use an older one. We might be able to post it as a bug in LaunchPad to get on the next version or at least get dev attention.

---

### Post by shmendrik on 2007-12-05
I had the exact same problem on a Powerbook pismo / firewire g3.

Nor could I find any help either. I had thought maybe this was because I put a dvd burner in the thing... but i guess not!

I went ahead and went back to gentoo linux which I had tried out a few years ago.

I can report that I have xfce running, wireless with airport and WEP, sound, and video so far. A dvd i threw in there even worked in mplayer.

Have not tried burning to the dvd or cd yet, but everything else is fine.

It is a bit of a long process, the install, but if you can follow the very good instructions they have, not very hard. I'm no linux geek.

The only hint of trouble was upgrading to python2.5... the package manager runs on python, so you have to be careful doing that...

---

### Post by newbiexubunt on 2007-12-05
> **flickerfly said:**
> I'm thinking that the Lombard just isn't supported on the newer versions of Ubuntu. I had a similar problem with Gentoo a couple years ago when they forgot to include the CD driver in one version of the install CD and I had to use an older one. We might be able to post it as a bug in LaunchPad to get on the next version or at least get dev attention.

well, maybe we can use a earlier vesion of xubuntu.  woud that work?:)

---

