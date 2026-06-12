---
title: "Would it be easy to go back to Windows if I decide I don't like Ubuntu?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by J. Eason on 2008-03-05
If I install Ubuntu and find I don't like it is it easy to go back to Windows without wiping out my hard drive?

---

### Post by uberlube on 2008-03-05
Well you have 2 options.
1) Take a look around the live cd and see if you like what you see.
2) Make a partitions for Ubuntu and do a dual boot. Then If you dont like it you still have windows.

---

### Post by billgoldberg on 2008-03-05
If you install ubuntu, it's on the harddrive.

You can dual boot that way you can use both operating systems (not at the same time, you'll need to pick wich one to start at boot up).

You can run ubuntu (or xp) in a virtual box (I use virtualbox, others use vmware)

However, just run the livecd for a while to see if you like it.

The live cd give you an idea of the OS. 

If you install it you'll have alot more options off course.

---

### Post by kellemes on 2008-03-05
> **J. Eason said:**
> If I install Ubuntu and find I don't like it is it easy to go back to Windows without wiping out my hard drive?


Yes, basically you only have to reinstall the Windows-bootloader, depending onn the Windows version this is a peace of cake.
Second step can be to delete/wipe the partition(s) Ubuntu uses so you can use them for other purposes.

---

### Post by uberlube on 2008-03-05
Also if you want to make a partition for ubuntu make sure you defragment your windows before you do it. Then resize your windows partition to make it smaller so you have room. And make sure you use the manual partition editor in the install and not the guided, because that will reformat your whole HD.

---

### Post by mikeyphi on 2008-03-05
> **J. Eason said:**
> If I install Ubuntu and find I don't like it is it easy to go back to Windows without wiping out my hard drive?

Yes - you just need to fix the MBR which points to your OS. Ubuntu overwrites the windows MBR on installation. Windows recovery will action the fix.
You can also just try the LiveCD without installing; just accept that the system is slower because it is not installed.

---

### Post by kpkeerthi on 2008-03-05
Or play with ubuntu using [vmware]("http://www.vmware.com")

EDIT: Oops! I'm blind.

---

### Post by J. Eason on 2008-03-05
I think I'm going to dual boot because I'm familiar with that.  But when I decide on an OS do I just delete the partition of the on I want to get rid of?

---

### Post by mikewhatever on 2008-03-05
> **J. Eason said:**
> If I install Ubuntu and find I don't like it is it easy to go back to Windows without wiping out my hard drive?

It depends on how you partition the drive. Make a separate data partition, so that deleting Ubuntu and reinstalling Windows would not affect your files.

---

### Post by ByteJuggler on 2008-03-05
You might also keep an eye on/try [WUBI]("http://wubi-installer.org/").  (Note I've not tried this myself yet, but it's apparently dead easy to use.)

---

### Post by J. Eason on 2008-03-05
How do I do that, exactly?

---

### Post by uberlube on 2008-03-05
Resize your windows partition. Then with the unused space leftover make a swap partition that is 2wice the size of your ram. Then With what is leftover make an ext3 partition and mount / on it. / stands for root.

---

### Post by 3rdalbum on 2008-03-05
You will, but if you delete Ubuntu you will need to go to a Windows recovery CD and run the "fixmbr" program.

The third option is Wubi - it's an installer for Ubuntu that will install it into a file on your existing Windows partition, but it will run directly on the hardware like a dual-boot. To delete Ubuntu, you'd just delete the file. But to delete Windows, you've also got to reinstall Ubuntu directly on your hard disk.

---

### Post by J. Eason on 2008-03-05
What about putting Ubuntu files on my external hard drive? Wouldn't that be the same thing as a partition?

---

### Post by aysiu on 2008-03-05
If this is the kind of question you're asking, you should seriously consider [installing Ubuntu as a virtual OS inside of Windows](http://www.psychocats.net/ubuntu/virtualbox).

---

### Post by ericartman on 2008-03-05
I also recommend Wubi. It's how I got my wife used to Linux and eventually she switched. I dual boot myself, but then I'm a gamer. I have a small 200 gig partition for windows and Wow and left 500 gig for Ubuntu which is what I use for my day to day computing. Dual booting has been rock solid since day one and answers my needs.

Cart

---

### Post by jryprt on 2008-03-05
Wubi is a great way to start out

---

### Post by vishzilla on 2008-03-05
Firstly try the Live CD, if you're still not convinced, I recommend to virtualize Ubuntu in Windows. Virtualbox, Wubi can do that

---

### Post by J. Eason on 2008-03-05
One last question, The software that I use on (and is compatible with) windows, will it work with Linux?

---

### Post by aysiu on 2008-03-05
> **J. Eason said:**
> One last question, The software that I use on (and is compatible with) windows, will it work with Linux?
Do you use open source software like Thunderbird, Firefox, FileZilla, Audacity, GIMP, OpenOffice, and Scribus? If so, yes.

If you use software like AutoCAD, Outlook, Microsoft Office (advanced features), inDesign, and iTunes, then, no. But you may be able to find equivalents:
[http://www.linuxappfinder.com](http://www.linuxappfinder.com)

---

### Post by vishzilla on 2008-03-05
Which software? Wubi runs on Windows only. Virtualbox runs on both WIndows/Linux

---

### Post by jseiser on 2008-03-05
you could always try going up to your local PC repair shop, and asking if they have a spare 20GB, 40GB HD, something cheap and small.

Pop our your windows HD, and stick in this new one, try ubuntu, if you dont likeit, rip that HD out, put back in your windows one, and everything will be the same.  er, you can leave the drive in, just disc. it or something :)

---

### Post by Kithmal on 2008-03-05
I'm going to pop in and ask a really quick question regarding going back to windows and such- Do you need a bootloader (Like GRUB) in order to switch back and forth between Windows and Ubuntu?

(/end derailment)

---

### Post by aysiu on 2008-03-05
> **Kithmal said:**
> I'm going to pop in and ask a really quick question regarding going back to windows and such- Do you need a bootloader (Like GRUB) in order to switch back and forth between Windows and Ubuntu?

(/end derailment)
Yes. Wubi adds Ubuntu to Windows' boot loader. A regular Ubuntu installation adds Windows to Grub (Ubuntu's boot loader).

The exception would be a virtual installation.

---

