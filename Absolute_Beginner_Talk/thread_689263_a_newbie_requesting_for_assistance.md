---
title: "a newbie requesting for assistance"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by kraddark on 2008-02-06
Good Day!

I am an aspiring Ubuntu LINUX user but as a complete newbie, I would like to ask those who have in-depth knowledge of linux to assist me (please..:confused:).

I would like to provide to guys with the specs of my computer

Motherboard: Intel DG31PR 
Processor: Intel Core 2 Quad Q6600
Video Card: ATI X1650 PRO 128BIT DDR3
NIC: Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC (this is on board)
Sound: Realtek High Definition Audio (this is on-board)
Memory: 1GB Kingston PC-667

Add-ons:
HP Deskjet d1460 printer
D-Link Airplus G DWL-G122 Wireless USB Adapter (rev. C)
D-Link DIR-300 wireless router

Here are my questions:

1. Is the latest version of Ubuntu which is 7.10, compatible with my hardware?
    If yes, is there someone here generous enough to provide me with the installation instructions?     (something printable would be very much appreciated).. Of course if the answer is no then I think I'm Out of luck......:cry:

2. Since i only have my hardware drivers for the windows OS, can someone provide me with the drivers I need for the installation of my hardware in LINUX and also the installation instructions.

I read a lot of articles concerning LINUX and I'm really impressed.. that's why I'm planning to switch to LINUX if given a chance. I also read that tech support for the UBUNTU Linux OS is the best here.

Please assist me regarding this one so that when I get a positive reply, I can start downloading the OS
right away.

Thank you so much for the time in reading this post.. Hope to get replies from you people soon.. O:)

---

### Post by Golem XIV on 2008-02-06
The best idea is to get a Live CD, boot from it and see if everything works.  You can get Live CDs for all major Linux distros, so you're not limited to Ubuntu.

Note that the Live CD system runs from CD and will be significantly slower than an installed system.

---

### Post by ibizatunes on 2008-02-06
Have u tried using a live cd image and seeing if you can get your hardware to work there.....
printer, you pretty much plug in and they work
wireless is more tricky, boot on a live CD and see if your wireless work....
General rule of thumb, Older hardware normally works fine in ubuntu 7.10....

---

### Post by Algus on 2008-02-06
Ubuntu comes with a lot of the drivers you'll need out of the box.  Download the Ubuntu ISO, burn it to a CD, and then stick it in your machine and reboot.  You can run the OS straight from the Live CD and see how it interacts with your hardware and spot some problem areas.  

You might find[ this]("http://apcmag.com/node/5162/") to be a useful read if you want to keep your Windows install

---

### Post by emarkd on 2008-02-06
The best thing you can do is [download the Live CD]("http://releases.ubuntu.com/7.10/") from Ubuntu and boot from it.  This will tell you what you're up against with your hardware, and your ATI video may be a bit of a hurdle.  If you want to read through the installation procedure before you start, check [this]("https://help.ubuntu.com/community/GraphicalInstall") out.

---

### Post by Trail on 2008-02-06
As said, the best idea is to download the live cd, throw it in the cdrom, reboot, and see if it works. You can then install graphically through the live-cd. It's pretty easy, but look at the ubuntu wiki if you are in doubt.

Linux does not really use drivers as windows, but instead the linux kernel, which is a quite big binary, has the information to access your hardware. So it will either work immediately, or it won't work. The exception would be some graphic cards, for which you'll need to use the restricted drivers manager to fully utilise them.

---

### Post by kraddark on 2008-02-06
woah, thanks a lot the reply was certainly in an instant.. regarding the live cd what type  should i use for my computer is it the x86 or the 64bit? and will this change the settings on my computer or it is like an OS that you can run directly from the cd but will not do any changes after you restart the computer? Sorry for being such a complete newbie..

---

### Post by Trail on 2008-02-06
It won't affect anything on your computer (unless you ask it to of course :P)

x86 = 32 bit. Depends on your machine I guess. But a 32bit version works for a 64bit CPU, but not the other way around. Generally 32bit is more well supported.

---

### Post by emarkd on 2008-02-06
The Live CD will NOT effect your hard drive uless you tell it to.  You can run the entire operating system from the CD and see how it works for you (it'll be a ltitle slow, though, because your CD is a lot slower than your hard drive).

---

### Post by kraddark on 2008-02-06
how would i know if im using x86 or 64bit?

---

### Post by emarkd on 2008-02-06
If you're talking about the Windows that came with your computer, its 32 bit, I'm sure.  64-bit ihas traditionally been used on high-performance server applications because you have to have 64-bit OS to address more than 4-gigs of RAM.  The 64-bit version of Linux will run a little faster if you hunt out 64-bit versions of the software you want to run, but the 32-bit is much better supported.  Unless you're planning to add more than 4-gigs of ram, you're probably safer with the 32-bit version.

---

### Post by kraddark on 2008-02-06
thanks a lot i'm gonna download that right now and inform the forums about the results.. thanks a lot for all who replied on my post.:)

---

### Post by bigred1 on 2008-02-19
32 bit is still more common, so that's more likely. In any case, the 32-bit Ubuntu will work on a 64-bit system, so you may as well choose that. 

You can also google for your CPU name to see the specs on it. To find your CPU name, in Windows, right-click MyComputer->Properties->Advanced, and see what appears after "Computer:"

You can also get this info from your BIOS, which is accessed right after you restart you computer.

---

### Post by hyper_ch on 2008-02-19
next time please use a descriptive thread title and not a generic "need help". That makes it easier to help.

---

### Post by Teber on 2008-02-19
your cpu seems 64 bits to me. in case of doubt 32 bits will always be safe. some people will opt for 32 bits anytime. although, you might test it with a live cd?

---

