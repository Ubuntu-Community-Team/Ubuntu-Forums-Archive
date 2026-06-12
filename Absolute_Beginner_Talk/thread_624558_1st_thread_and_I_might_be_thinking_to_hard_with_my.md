---
title: "1st thread and I might be thinking to hard with my search"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by soulful1 on 2007-11-27
I've searched and I just think that my wording may be off. I want to run Linux but I'm in still in school and I still need certain MS functions (i.e. Office and Visual Studio.NET 2003) and I was wondering if there was a way that I can load Ubuntu on my computer while keeping Vista (without using a Live CD).

---

### Post by xyz on 2007-11-27
Sure you can [dual boot.]("http://users.bigpond.net.au/hermanzone/")

Don't hesitate to come back here with questions and welcome!

---

### Post by kpkeerthi on 2007-11-27
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

All the best.

---

### Post by soulful1 on 2007-11-27
I just read the one from APC and think that is the one I can follow but my question is how much does shrinking Window's partition affect performance?? I am hoping for equal performance on both OS..am I asking for too much?

One more question..because  I'll be running both, would I have to download the 32bit version. I downloaded the 64bit already and would just like to know.

---

### Post by kpkeerthi on 2007-11-27
I can't really help you with how much shrinking you need to do as it really depends on how much space you want to keep for windows. Shrinking should not affect performance as long as there is enough room for the system to run. 

As for choosing the version, see 
[https://help.ubuntu.com/community/ProcessorArch](https://help.ubuntu.com/community/ProcessorArch)

---

### Post by soulful1 on 2007-11-28
OK...i have done everything and I've tried to install but after everything loads, I just get a glowing screen and it turns white then black. What the F is going on:(

---

### Post by soulful1 on 2007-11-28
Got Dern The The Top...

I wouldn't worry too much but I'm in the process of doing it now and I'm getting the same thing... *shrugs*

---

### Post by soulful1 on 2007-11-28
*waving trying to see if anyone notices*

---

### Post by RomeReactor on 2007-11-28
Hi. What processor and video card does your system have? when you say that everything "turns white then black",  do you get white text on a black background (see attachment)?

---

### Post by soulful1 on 2007-11-28
I don't even get that far..right after it seems  like things are loads (checks everything and says ok) right after, its like the screen is blacks, starts to brighten up to whitish grey then fades back to black and does nothing. 

I have a Compaq f730us

AMD Athlon™ 64 X2 TK-55
NVIDIA GeForce  GO 6000M

---

### Post by louieb on 2007-11-28
> **soulful1 said:**
> OK...i have done everything and I've tried to install but after everything loads, I just get a glowing screen and it turns white then black. What the F is going on:(
I absolutely have no clue where your installation effort is crapping out so.

Do you get a screen with 5 or 6 options listed?  
If yes then have you run the option **check media for defects**? or some such.
Did it report errors?

Get back and we'll go from there.

---

### Post by RomeReactor on 2007-11-28
The problem might be related to ACPI; try [this thread]("http://ubuntuforums.org/showthread.php?p=3780022").

---

### Post by soulful1 on 2007-11-28
I boot the computer with the disk, the Ubuntu screen comes up. I check for defect, reboot, then hit enter on the "Start or Install..." option. It loads and then stops...the screen start changing colors and nothing happens.

---

### Post by louieb on 2007-11-28
Damn hoping for something easier, Like a bad CD burn.
Your going to have to play around with boot options now.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

If your PC has on-board video  plug your monitor into it and see what happens. I suspect Ubuntu not configuring your graphics card. 

Also another thing to look at is during the boot process press Ctrl+Alt+F1
that will list the startup messages. May find a clue there.

---

### Post by soulful1 on 2007-11-28
RomeReactor..I appreciate the link..that was the problem but now I'm facing another delimma. I go through the whole setup and and I get to the ready to install screen. i look at the "Ready to Install" screen and I look under the Migration Assistant and I don't get the "Windows Vista/Longhorn.."seetting. What should I do about this?

---

### Post by soulful1 on 2007-11-28
*sneaking thread to the top*
lol...I can't wait til I finally get settled..

---

### Post by soulful1 on 2007-11-28
Yall might think I'm crazy but I'm not trying to let this get to the bottom...I'm really trying to get this and I'm having the hardest time getting past this first step..:(

---

### Post by Tomosaur on 2007-11-28
Ok, let's see what we can do:

1) The LiveCD loads incredibly slowly on many people's computers, and can look like it's crashing or something (my screen becomes very garbled just before the desktop loads on the LiveCD, for example). When Ubuntu is installed, these problems usually disappear.

2) The Migration Assistant - I'm not sure if it even works properly with Vista yet. If you're going for a dual boot, you SHOULD technically be able to just access your Vista partition and so keep all your documents and stuff.

Before you continue, though - it's worth backing up everything you want to keep. Errors are unlikely during the installation, but it's worth making sure you have backups (on USB sticks, external drives, CDs, whatever) just in case.

Another trick people sometimes use is to create an extra partition, formatted as FAT32, and to just use that for documents, music and stuff, since both operating systems should be able to read and write to that just fine. Basically what I'm saying is just forget about the migration assistant if you're going for a dual boot setup.

---

### Post by MrSpiffdifilous on 2007-11-28
Like Tomosaur said, not sure if the migration tool works with Vista yet however, you should have no trouble accessing files on you Vista partition within Ubuntu. Even if your Vista partition is formatted NTFS Ubuntu will read it as well write to it. I personally have Ubuntu running on a 45Gb partition (ext3) on a 250gb SATA drive, the other 205Gb are NTFS. I also have 3 other hard drives and I have full access to all of the files on each of them. 45Gb is enough for Ubuntu to run very nicely on my computer and I have a fairly dated processor. Every once-in-a-while I have to clear the cache files. 

  What I'm trying to say is dont worry about Migration but DEFINITELY back up anything you cant afford to lose in the strange even that your disk fails. 

Welcome to the forums

---

### Post by jken146 on 2007-11-28
45GB is a bit big IMO.  Of course, it depends on what exactly you put there, but for the typical user 10GB for / is probably ample.  I don't think the install takes up more than about 3-4 gigs.

---

### Post by soulful1 on 2007-11-28
> **MrSpiffdifilous said:**
> 
  What I'm trying to say is dont worry about Migration but DEFINITELY back up anything you cant afford to lose in the strange even that your disk fails. 

Welcome to the forums
So will the bootloader still load showing both Vista and Ubuntu. I ask because I will still use both of them equally. Vista because I'm in school and all of my documents are on there, more importantly Visual Studio and Ubuntu because after I graduate, I will run Linux completely but I'm counting this as my learning process. What is it call, GURB. GRUB...lol..will it Vista and Linux both show up.

---

### Post by jordanmthomas on 2007-11-28
Yes, the bootloader (GRUB) will show Ubuntu, a rescue-mode Ubuntu, a memory-test, and Vista at the bottom.

---

### Post by ray bot on 2007-11-28
Yeah, the Ubuntu installer usually does a pretty good job of detecting other operating systems and adding them to your grub menu.  After installing Ubuntu, you should get a menu at startup that lists both operating systems, and you can choose whichever one you want to boot.

---

### Post by soulful1 on 2007-11-28
Thanks!!!

Yall are great!

---

