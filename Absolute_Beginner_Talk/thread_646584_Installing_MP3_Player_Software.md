---
title: "Installing MP3 Player Software"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-12-21
Hey everyone,

I'm pretty much a noob to the whole lynix operating system.
I got an mp3 player for Christmas by CREATIVE, and the mp3 player itself is called ZEN V PLUS.
They gave me an installation CD, but it does not work.
Would anybody know how to install this thing?

Any advice would be greatly appreciated.

Thanks

---

### Post by chips24 on 2007-12-21
does it use an .exe prefix to install it? because execution files dont work on linux

---

### Post by cool_penguin on 2007-12-21
hey dude, you should be able to plug it into the USB port of your computer and Ubuntu will automatically mount it as a removable disk. (if the player has MSC mode) and then you can start copying all the mp3 files that you like,. 

Cheers,
harry

---

### Post by kahram.yoon on 2007-12-21
hey 
i would try to plug the mp3 in through the usb but the installation manual says to absolutely not plug in the mp3 until i installed it.

as to whether it's an .exe file or not
i have no idea to even figure that out
can anybody point me in the right direction?

---

### Post by kahram.yoon on 2007-12-21
> **chips24 said:**
> does it use an .exe prefix to install it? because execution files dont work on linux

im not sure if this will help or not
but when i put the cd in
a folder opened up and there's one icon that says setup.exe
does that help?

---

### Post by cool_penguin on 2007-12-21
You dont seem to get the point dude. Thats the manual for Windows users. Those rules are  not applicable in the Linux world. Go ahead and plug it in. If it does not work as i said (as MSC device), there is yet another method for getting it to work with Ubuntu.

Cheers,
Harry.

P.S: Please forget all those junk windows rules and methods. You are now at a level higher.

---

### Post by cool_penguin on 2007-12-21
Forget the .exe file. As i mentioned you dont need the CD if you are using Ubuntu, If i were you, i would just keep the CD aside or throw it in the garbage. That CD is for Windows users.

---

### Post by PeterJS on 2007-12-21
> **chips24 said:**
> does it use an .exe prefix to install it? because execution files dont work on linux

Yes and no. It's a matter of lazy windows nomenclature (exe is *an* executable format, not *the* executable format), .exe is generally associated with the windows portable executable format, which linux doesn't natively handle, but can be run under win. To say that linux doesn't handle executable formats is patently false, and kind of silly. If linux didn't handle executable formats it couldn't run any programs at all. There are in fact two executable formats used by linux ELF and a.out. a.out is an older format that is being phased out in favor of elf, but still gets used from time to time in legacy stuff, and quick and dirty hacks.

And back to the topic of the thread at hand, I don't know how Creative Zen's work, but you might try just plugging it in and seeing what happens. If it's just a usb disk with music on it, then you won't need to install anything.

---

### Post by kahram.yoon on 2007-12-21
ok
i plugged in the mp3 with the usb
but nothing is happening
what do i do next?

---

### Post by PeterJS on 2007-12-21
Open nautilus (Places > Computer), is there a new hard drive shown with a name that looks like it might be your Zen?

---

### Post by kahram.yoon on 2007-12-21
ok

i clicked places and then computer
i don't see a nautilus tho

i see a floppy disk folder
cd rw/ dvd rw drive folder
and a file system folder 

the only folder it let me open was the file system folder and i clicked one folder that stood out (initrd.img);  but then the computer told me that it cannot support that type of archive file

---

### Post by PeterJS on 2007-12-21
Nautilus is the name of the program that opens when you click on Places > Computer. So it looks like it didn't load up like I'd hoped. Have you searched the forums? I'll see what google can dig up.

Initrd.img has nothing to do with the task at hand. What initrd.img (**init**ialization **R**am **D**isk **im**a**g**e)  is an archive of the bare minimum set of drivers needed to start the system to point that it can read the hard drive and load the rest of the drivers for the system.

---

### Post by PeterJS on 2007-12-21
Ok, I've got an answer for you. I started with:
[http://www.google.com/search?q=Ubuntu+Creative+Zen](http://www.google.com/search?q=Ubuntu+Creative+Zen)

Which led to this:
[http://ubuntuforums.org/showthread.php?t=216191](http://ubuntuforums.org/showthread.php?t=216191)

And finally a zen understanding of working with a Zen. You'll want to install [gnomad2]("apt:gnomad2").

---

### Post by kahram.yoon on 2007-12-21
yes!
it finally works
thank you everyone for all your help

---

### Post by kahram.yoon on 2007-12-26
It works but I am having some problems with it.
When I upload songs to my zune, some songs don't show up.  They show up on my zune as "unknown" songs and artists and do not even show up on my zune.  Anybody know what is going on?

---

### Post by rainwalker on 2007-12-26
> **kahram.yoon said:**
> It works but I am having some problems with it.
When I upload songs to my zune, some songs don't show up.  They show up on my zune as "unknown" songs and artists and do not even show up on my zune.  Anybody know what is going on?

Zunes, I don't know about. But if it's editing song data, you should use tagtool (search Synaptic Package Manager for it) to change the data, it rocks.

---

### Post by kahram.yoon on 2007-12-27
i searched add/remove programs for synaptic package manager and I have it but how do I search within it to find tooltag?

---

### Post by rainwalker on 2007-12-27
It's under System > Administration > Synaptic Package Manager

Synaptic is the main way to install software on Ubuntu. If anyone ever tells you to install a certain package, you're almost always going to do it with Synaptic.

---

### Post by lyceum on 2007-12-27
Just in case anyone has a Creative Zen (no letters or anything after it) Gnomad 2 does not find it. I think it is too new. It is a great little player though... if I could only get it to connect... :confused:

---

