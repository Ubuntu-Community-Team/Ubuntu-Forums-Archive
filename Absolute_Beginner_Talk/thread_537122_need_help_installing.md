---
title: "need help installing"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by M@TR!X on 2007-08-28
hi im having trouble installing Ubuntu 7.04 or w.e the newest one is. i just bought the CD from amazon.com And when i put the CD into my CD drive and load it , adter i click Start or install ubuntu it get to the part where its says
loading somehting                                          [ok]
loading somehting else                                   [ok]
and all that and then after about 2 minutes the screen turns black and nothing happens...my computer is on right now at that blank screen and has been there for about 30minutes now can any please tell me what i did wronge or what i still have to do 
that you!

---

### Post by kellemes on 2007-08-28
I would try the alternate desktop CD.. you can download it [here]("http://www.ubuntu.com/getubuntu/download") You just have to tick the checkbox on the bottom.

Just in case you didn't know..
By the way, you don't have to buy Ubuntu, you can download it for free and also it can be shipped to you for free. [See here]("https://shipit.ubuntu.com/").

---

### Post by mlentink on 2007-08-28
You actually ***bought*** a cd? Like in paying real money for it? Gosh, you're motivated!

You might help us help you by providing a few details. What kind of a machine are you trying to install ubuntu on? Processor, memory, graphics card etc? What version of ubuntu are you trying to install?

---

### Post by M@TR!X on 2007-08-28
ok i only bought it becasue i wanted it fast :lolflag: and im trying to install on a HP Pavilion tx1000z i forgot what the graphics are and the processor is AMD Turiton64.x2  2G ram and i just deleted my recovery partition to make it have a 111GB hard drive
ubuntu 7.04

---

### Post by oilchangeguy on 2007-08-28
> **M@TR!X said:**
> ok i only bought it becasue i wanted it fast :lolflag: and im trying to install on a HP Pavilion tx1000z i forgot what the graphics are and the processor is AMD Turiton64.x2  2G ram and i just deleted my recovery partition to make it have a 111GB hard drive
ubuntu 7.04

you can't get much faster. than being able to download it from the ubuntu website. and you deleated your recovery partition, that probably was not the smartest move. i hope you've got a recovery cd, in case you need it.

---

### Post by mlentink on 2007-08-28
OK, fair enough. As long as you know that you don't have to pay for Ubuntu. 
Welcome to the free world!

Now as to your installation issue, I am bit sorry to hear you deleted that recovery partition. Ubuntu doesn't need it, but Windows does. Ok, done deal.
Am I correct in assuming you installed the 64-bit version? Did it run the LiveCD at all? Quite frankly, with specs like that it should....

---

### Post by M@TR!X on 2007-08-28
yes it started to install but then it like froze or soemthing the screen is just blank...yes i have a set of recovery discs and i deleted the partition so i could dual boot

---

### Post by ryanawall on 2007-08-28
Hi, I have a HP Pavilion DV6000 (same processor), this is how I installed Ubuntu. Download the 32 bit version and burn the iso to a cd (slow speed like 8x) Then boot up using this cd. When you get to the screen where it says run/install Ubuntu, memory check, check for defects, etc. Press F5 (I think it's F5) for other options. Then type "noapic" without the quotes. And then run/install. This should get you into the live cd GUI (Graphical User Interface) and click install. After that just follow the on screen instructions. Hope this helps!

---

### Post by M@TR!X on 2007-08-28
yea well im using the alt cd soo...so far its working

---

### Post by ryanawall on 2007-08-28
Let us know if you have any luck with it!

---

### Post by M@TR!X on 2007-08-28
omfg kk it installed good and everything but when i rebooted my computer and choose to startup ubuntu it crashed there was a screen with a bunch of colors and thats it like the screen just messed up anyone know what this is???

---

### Post by M@TR!X on 2007-08-28
ok i rebooted again and when the ubuntu load screen pops up the status bar loads fully but then the screen goes blank and thats it...just black and nothing happens...answer both questions please:(:mad:


When i startup Vista it loads regularly...help!!!i need ubuntu to work!!!im sooo despeate!

---

### Post by ryanawall on 2007-08-28
Personally, I couldn't tell you what happend. However, what I would do is to just attempt another install using the 32 bit version iso and type "noapic" in other options before continuing the install.

---

### Post by M@TR!X on 2007-08-28
kk umm when i reboot for a third time it says Bios bug something bug found???

---

### Post by ryanawall on 2007-08-28
Would it happen to say "PCI BIOS BUG FOUND" by any chance?

---

### Post by M@TR!X on 2007-08-28
im not sure because im reinstalling it...what happens if it did say that???:confused:

---

### Post by ryanawall on 2007-08-28
From what I understand nothing fatal, if you need to fix it after your finished installing then you just recompile your kernel and under the pci access mode option choose direct instead of any. For help on how to recompile a kernel see:
[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

---

### Post by M@TR!X on 2007-08-28
ok thank you ill tell you how the reinstallation went :)

---

### Post by M@TR!X on 2007-08-28
ok i reinstalled and the same thing happens!!! the thing did say PCI Bios bug found and some numbers umm can you tell me your msn or aim screen name or something because i kind of need step by step instructions on how to recompile or compile or w.e you told me to do...i dont understand it :confused: please help me :KS

---

### Post by dpar on 2007-08-28
Sounds to me like it's not using the proper video driver.

---

### Post by ryanawall on 2007-08-28
Well, I am at work right now(clearly I am not doing any "work"), so I can't get on AIM or MSN due to it not being available. If that link I sent you is a little hard to follow, your best bet is using google to find step-by-step instructions on how to recompile your kernel. Just remember all you need to do in it is: under the pci access mode option choose direct instead of any. Hope this is helpful.

 BTW now that you have reinstalled Ubuntu are you able to get  into the GUI?

---

### Post by M@TR!X on 2007-08-28
ok i installed it and it is working fine just one problem...im going to dual boot and i need help partitioning!!! lolz im in the ubuntu desktop and everyhting i clicked install and now im on step 4 of 7 partitioning

---

### Post by M@TR!X on 2007-08-28
in the screen it says my partitions here they are
 device name:/dev/sda1              type:ntfs          size:111612MB            Used:unknown
device name:/dev/sda2               type:ext3         size:8003MB                Used:2300MB
device name: /dec/sda5                type:swap       size:411MB                Used:0MB

and when i select device:/dev/sda2 and click next it says "No root file system defined please correct this from the partitioning menu


help!!!!

---

### Post by ryanawall on 2007-08-28
xp or vista?

---

### Post by M@TR!X on 2007-08-28
Vista

---

### Post by M@TR!X on 2007-08-28
ok i think i got it i just needed to mount the partiton as "/" thank you anyways...ill tell you if it worked and what i need help with :-):):lolflag:

---

### Post by ryanawall on 2007-08-28
OK, the best I know of so you don't lose your Vista data is to partition your hard drive in vista. First defrag. (I can't remember how to get there off the top of my head, but I'm sure you could figure it out. I do know that it is somewhere buried in the control panel). Then partition your hard drive by clicking start then typing dskmgt. This will show you how do partition it: 
[http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php]("http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php")
OK, now back to Ubuntu follow instructions (skip to step 6) found here [http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx")

That should be it. Hope it helps!

---

### Post by M@TR!X on 2007-08-28
ok it helped alot thank you!!! im now using the full version of Ubuntu!!!you have just helped create a Ubuntu user!!! omg thank you man like really...time to customize and stuff anyways do you know any cool things i could do? how do i enable desktop effects???when i click enable to enable it it says desktop effects could not be enabled??? do you know how to enable them or something?? if anything when i installed my graphics card it told me to restart that would be the problem...ill be right back im going to restart

---

### Post by ryanawall on 2007-08-28
One thing you might like: 
-Try searching google for gnome themes
On top of that the customization in unending literally considering Linux is open source. It all depends on what kind of things you want to do. But first I would go through and basicly test the system. Check things like if your wireless works or not, if you are even able to get online at all, (Firefox also has some nice themes and tons of addons just google it)
If you want to do something just google and there is almost always a how to; no need to reinvent the wheel right? Have fun with it, and remember it can be frustrating at times but not nearly as bad as things used to be with linux.

---

### Post by very_japi on 2007-08-29
I was having the same trouble in my 64bit box. I solved it using the alternate installation cd for the AMD64 version of ubuntu.

For some strange reaon any other flavour of installation would hang EXACTLY as you describe it.

---

