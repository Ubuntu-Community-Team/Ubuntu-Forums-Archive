---
title: "Mac&gt;Linux transition: questions re system backup, file transfer"
date: 2017-01-06
forum: Apple Hardware Users
---

### Post by joannacw on 2017-01-06
I'd like to test-drive Ubuntu on my elderly MacBook Pro. I do not understand computers well.  I've read that dual-booting is the best way to test Linux systems on other hardware; also that it's important to do a full system backup before partitioning the HD and installing Ubuntu on one side of the partition. I have a few questions whose answers are probably painfully obvious to most people:

Can I do a system backup onto a high-capacity thumb drive, or directly onto another elderly Mac computer, or is there some reason why I need to buy an external hard drive? 

I have Time Machine and Carbon Copy Cloner on my Mac. Can I use one of these for system backup or is Clonezilla preferable (if so, why)? Which backup method will make it easiest for me to transfer Pages files, photos, and web pages created in Mac OS X into Ubuntu?

Is downloading rEFInd the best way to go abut creating a partition? 

If I were to test-drive Ubuntu on another elderly Mac (iBook g4) instead of partitioning the hard drive, would this make it any harder (or easier) to transfer files from OS X into the Linux system? If I then decided that I wanted to run the MacBook Pro exclusively on Ubuntu, would the version of Ubuntu which would be best to run on the MacBook Pro be so different from that which would run on the iBook g4 that I'd have to reconvert all my files?

 I'm not interested in gaming or other highly specialized applications. I want to be able to create word processing documents and spreadsheets, store and edit photos, and create and revise web pages. My website is already hosted in Linux form, but I've created and maintained it on my computer in iWeb. I'm not sure if I can directly transfer the iWeb site or if I should just download the page directly from the hosting site into Ubuntu. It would also be nice to be able to view videos (from the Web or DVDs.) I don't foresee needing to create/edit videos.

Is there a model of Ubuntu which you'd especially recommend for the applications above, and for a person with very limited technical understanding?

Thank you for your patience with these raw beginner questions.

---

### Post by howefield on 2017-01-06
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by joannacw on 2017-01-06
Thanks for the move. Sorry.

---

### Post by &amp;KyT$0P# on 2017-01-06
> **joannacw said:**
> Can I do a system backup onto a high-capacity thumb drive, or directly onto another elderly Mac computer, 
I don't see why not, as long as they've got enough space.

> I have Time Machine and Carbon Copy Cloner on my Mac. Can I use one of these for system backup or is Clonezilla preferable (if so, why)?
Use Time Machine to back up Mac OS.  It's easy to use and backs up the entire system.

> Which backup method will make it easiest for me to transfer Pages files, photos, and web pages created in Mac OS X into Ubuntu?
As I know from personal experience, you will not be able to read a Time Machine backup in Ubuntu.  I don't remember what I ended up doing to move my stuff, sorry.

You could move your stuff onto an external drive, then copy it into Ubuntu.  I'd guess I probably did something along those lines.

> Is downloading rEFInd the best way to go abut creating a partition? 
rEFInd is not related to partitioning.  It's needed to load GRUB, which boots Ubuntu.  And with dual-boot, rEFInd lets you choose between loading GRUB or booting Mac OS.

Only modify the Mac OS partition from within Mac OS, using Disk Utility.  In the Ubuntu installer, select "Something else" and manually create your Ubuntu partition(s) there.

> If I then decided that I wanted to run the MacBook Pro exclusively on Ubuntu,
Don't.  I needed Mac OS in order to set up my Ubuntu, and have needed it every so often as part of troubleshooting.

---

### Post by joannacw on 2017-01-06
Thank you very much! That answers most of my questions very helpfully. Sorry for my confusion about rEFInd. I understand better now. And it's good to know that keeping OS X is helpful even if you're primarily using Linux. 

Anyone have suggestions about file transfer (Pages word processing files, photos now in iPhoto, website on my machine in iWeb and on our hosting site in Linux) into the Ubuntu system?

---

### Post by ian-weisser on 2017-01-06
Welcome to a fun world of learning and adventure!

> **joannacw said:**
> I've read that dual-booting is the best way to test Linux systems on other hardware
You do not need to install Ubuntu to test it.
You merely need to create LiveUSB, and to boot from it.
Dual-booting is not easy, and not supported by Apple.

> **joannacw said:**
> Can I do a system backup onto a high-capacity thumb drive, or directly onto another elderly Mac computer, or is there some reason why I need to buy an external hard drive?
There are two types of backups: Data-only and whole-system. Time Machine and Clonezilla backup the whole system. The problem with whole-system is that it can be difficult to restore from those backups to a smaller drive (since half the drive will be Ubuntu). Whole-system backups appeal to users who lack an install disk, or who have highly-customized systems.
In the Linux world, the installer is freely available, so many of us backup our data only.

> **joannacw said:**
> Anyone have suggestions about file transfer (Pages word processing files, photos now in iPhoto, website on my machine in iWeb and on our hosting site in Linux) into the Ubuntu system?
iPhoto, iTunes, iWeb, and other Apple-specific products often lack an easy way to migrate your data out of those products. This is known as 'vendor lock-in,' and is deliberate by Apple. Not much we can do about it - you paid extra for that feature.

---

### Post by joannacw on 2017-01-06
Thanks very much! Just trying to make sure I understand: does "[COLOR=#000000]You merely need to create LiveUSB, and to boot from it."  [/COLOR] mean I need to install Ubuntu on a USB drive and boot from that? I've read that CD booting leads to slower function than hard-drive booting... is the same true of USB booting? If so, do you recommend transitioning completely from Mac OS X to Linux if I like how Linux works, rather than retaining both OS X and Ubuntu on one computer as Halogen2 seems so be recommending?

---

### Post by &amp;KyT$0P# on 2017-01-06
> **joannacw said:**
> Thanks very much! Just trying to make sure I understand: does "[COLOR=#000000]You merely need to create LiveUSB, and to boot from it."  [/COLOR] mean I need to install Ubuntu on a USB drive and boot from that? 
No.  When you boot the Ubuntu install media, you should be offered two options: "Try Ubuntu" and "Install Ubuntu".  What ian-weisser is suggesting is that you select "Try Ubuntu" and, er, try stuff out to see if it works for you.  Good advice, that. :)

> If so, do you recommend transitioning completely from Mac OS X to Linux if I like how Linux works, rather than retaining both OS X and Ubuntu on one computer as Halogen2 seems so be recommending?
This isn't an either-or.  If I were to switch to non-Apple hardware next week, I wouldn't need Mac OS at all.

---

### Post by joannacw on 2017-01-06
Ah, now I see. Thank you!
So long as you use Mac hardware you do find that it's worthwhile to partition the HD and retain OS X as well as Ubuntu?

---

### Post by &amp;KyT$0P# on 2017-01-06
You're welcome.

> **joannacw said:**
> So long as you use Mac hardware you do find that it's worthwhile to partition the HD and retain OS X as well as Ubuntu?
Absolutely.

To be more specific, I needed it for setting up graphics in Ubuntu.  And for reinstalling rEFInd when I screwed that up.  And to help troubleshoot something I thought could be a hardware issue.... and the list goes on.

You won't always know in advance when you'll need Mac OS, but as long as you've got it around you won't be caught out when the time comes.

---

### Post by joannacw on 2017-01-07
Thank you again!

---

