---
title: "Apple hard drive wont boot on a G3 iBook"
date: 2008-12-25
forum: Apple Hardware Users
---

### Post by metroidnemesis13 on 2008-12-25
Okay, so I know you guys are only supposed to help with Ubuntu, but I'm fed up.  You all probably know a lot about Apple's/Sun's open firmware.  Apparently no one on the apple forms does, and I'm having major problems booting a hard drive.  I can install OS X Tiger on it and the disc recognizes the hard drive, but it wont boot.  I've already tried reseting the nvram and defaulting settings, the apple option pr keys, and just about everything under the sun.  With all of your advanced knowledge about kernels and Unix, do you guys think you could help me?  You guys have helped me with something like this before when I had problems with a G3 desktop...

The link to the apple article is

[http://discussions.apple.com/thread.jspa?threadID=1835481&start=0&tstart=0](http://discussions.apple.com/thread.jspa?threadID=1835481&start=0&tstart=0)

P.S.  I'm using Ubuntu 8.10 right now on my laptop and on my desktop, and I'll never use Windows again.  Ever.  

Thanks.

---

### Post by mkvnmtr on 2008-12-25
I am no expert but it is a pretty good bet that your firmware doesn't support that OS and Apple is not going to provide it.

---

### Post by metroidnemesis13 on 2008-12-25
It's not the OS, it's the pre-packaged BIOS firmware.  It has to be compatible.

---

### Post by tiresia on 2008-12-26
Can you please tell us something more about the hardware - processor, ram, model (you can give us a link to [http://www.everymac.com/](http://www.everymac.com/))
If I understand:
You can start from the Tiger Installer-CD, you checked it and you installed it on your HD. Everything seemed to work well.
But when you restart after the Installation, the Computer shows you a question mark.
Is it so?

---

### Post by metroidnemesis13 on 2008-12-26
Yep, that's exactly right.  I have 128 MB of RAM, a 10 GB hard drive, and a 500 MHz PPC processor.

---

### Post by tiresia on 2008-12-27
OpenFirmware has nothing to do with your problem.
Tiger needs 256MB Ram as minimum system requirement
[http://support.apple.com/kb/HT1514](http://support.apple.com/kb/HT1514)

I'm not sure that it depends on it. 
I would try to install MacOS9 or Linux, in order to be sure that everything works correctly. If it's ok, you can think to purchase more memory for you computer.

---

### Post by metroidnemesis13 on 2008-12-27
I've already booted a hard drive with Tiger on this Mac so it has nothing to do with ram.  Plus, I've booted it with a 128 mb stick and nothing.  So it's not the ram.

---

### Post by tiresia on 2008-12-27
I guess, that this is your mac, right?
[http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html)
Yes, you must be able to run Tiger on those machines (and you confirmed me that you did it)

A first easy attempt to find a solution: can you please start again from the CD Installer and select there from the Utilities the StartUp Disk?

---

### Post by metroidnemesis13 on 2008-12-27
Yeah.  I can do that, but I've done it already before.  It finds the hard disk and I say start up the hard disk, and it restarts and then there's the folder with the question mark.

---

### Post by tiresia on 2008-12-27
It's quite strange, what you describe.
Is the HD, that one shipped with ibook?
Are you sure that the HD is ok?

If so, can you please do following:
start the computer and hit the cmd-opt-O-F keys to access Open Firmware.
Run 
```
printenv
```
and post here what you see beside boot-device, boot-file

Then run
```
reset-nvram
set-defaults
reset-all
```

The computer should restart.

---

### Post by metroidnemesis13 on 2008-12-27
Already did that, it doesn't do anything.  This HD is from a laptop, not sure what was on it before, but that shouldn't matter.   A PC ATA hard drive is identical to a mac hard drive, you just have to fiddle with the firmware.  I took a PC hard drive out of my collection and threw it in a G3 B/W and got it working.

---

### Post by tiresia on 2008-12-27
> **metroidnemesis13 said:**
> Already did that, it doesn't do anything.  This HD is from a laptop, not sure what was on it before, but that shouldn't matter.   A PC ATA hard drive is identical to a mac hard drive, you just have to fiddle with the firmware.  I took a PC hard drive out of my collection and threw it in a G3 B/W and got it working.

I know that. But a mac as no 'BIOS'. Open Firmware has a similar function as BIOS, but it is quite different. 
The point is, that if Open Firmware can't see the HD, the HD can't boot. That the Installer sees it, means that Open Firmware could recognise it.

Can you please post what you find after boot-device?
I would also try with another HD, if you have one.

---

### Post by metroidnemesis13 on 2008-12-27
The other one I have is completely dead, so this guy is my last.  Yeah, when I type printenv it lists a load of crap.  Next to boot-device it lists 
         
hd:,\\:tbxi   

     twice

---

### Post by tiresia on 2008-12-28
Question: when you installed, did you completly erase the hd?
It's quite strange, what happens with your HD.
There must be a problem with the HD or with the Installer CD.
Did you try to install MacOSX with that Installer on other Machines?


Try following:
```
dev hd
ls
show-children
words
```
What do you get from 'show-children'?
Does it list after words 'open'?

---

### Post by metroidnemesis13 on 2008-12-28
Yes I did completely erase it.  And yes, the installer CD does work.  If not, the Jaguar and Panther CDs should have done it.  

It doesn't recognize children as a word.

---

### Post by metroidnemesis13 on 2008-12-28
I'm beginning to think maybe the hard drive is just failing; it hasn't failed completely, but it's jacked up.  So, say if I just bought a new hard drive off of tigerdirect.com and threw it in there and installed OS X it would work and boot fine, without any firmware manipulation or magic?

---

### Post by tiresia on 2008-12-30
Yes, you don't need to do anything.
Open Firmware should recognise it. 
But before buying a new one, could you try the old one on an other mac?
Or can you try to install another os (macos9 for example)?

---

### Post by metroidnemesis13 on 2008-12-30
Yeah, I've tried it in two different Macs, and I've tried working hard drives in those and they booted.  I think I am going to try to install OS 9 although I'll have to find the disks.  Then I'll install OS X on top of that if possible.  If that doesn't work, I'll probably just wipe it completely and put it in a PC laptop and run Ubuntu.

---

