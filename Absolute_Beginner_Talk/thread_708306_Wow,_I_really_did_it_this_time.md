---
title: "Wow, I really did it this time"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by makebusy7 on 2008-02-26
Hello all 

Here's what got me to the Ubuntu forums 

5 months ago I bought a new HP Pavilion a6009n with the dual AMD processors and 8g RAM (aftermarket install) ... faster than what I was using prior ... except for this Windows Vista that was suddenly pissing me off.  

So I tried to install Ubuntu onto a 4g flash drive to run as an alternate OS.  You all might already know what happens next.  

My Vista was unbootable so I installed Ubuntu right over it. Cool right? 

I am impressed with what I have "seen" so far but as far as usability, I am a bit stumped.  I cannot install anything because I don't understand how.  It's not like windows where I would just click and it installs itself.  

I am not sure that I am getting the most from my video card.  I downloaded the LINUX drivers for my specific card and ... I can't make it work.  

I haven't even gotten to the printer yet and lets not get started on my external HDD containing all my media.  

If I partitioned my HDD with Ubuntu, is my Vista still there somewhere?  When I call HP, are they going to laugh at me? 

Should I turn back and forget this pretty new OS because I don't understand computers all that much?  

I see there is a a lot of help available and yes, I intend to read (some more) the posts and other available information. 

I'm special just like everyone else :)  and I wanted to share my special story with other :guitar: cool people 

See ya around on the boards and I hope that you all like me

---

### Post by philinux on 2008-02-26
Installing programs.

1. Applications - at the bottom you'll see Add and Remove.

2. System - Admin - you'll see synaptic package manager.

Have fun

---

### Post by sailor2001 on 2008-02-26
if you installed dual boot, the last os install will have the boot (grub) on it. At start-up screen you have the choice to let it start-up as ubuntu or arrow down to "other operating system)..The default can be changed quite easy if you start counting down the kernals on the boot screen starting with 0 to the kernal you want as default start-up.    In the terminal (accesories/terminal/) type gksudo gedit /boot/grub/menu.lst  give your password and change the menu list 'default 0 to what ever number you wanted to boot into. Click save and exit

---

### Post by makebusy7 on 2008-02-26
> **philinux said:**
> Installing programs.

1. Applications - at the bottom you'll see Add and Remove.

2. System - Admin - you'll see synaptic package manager.

Have fun


Thanks! :)

---

### Post by mali2297 on 2008-02-26
For installing programs, &#347;ee 
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

As for your video card, go to System -> Administration -> Restricted Driver Manager and see if there is a suitable driver available.

---

### Post by makebusy7 on 2008-02-26
> **sailor2001 said:**
> if you installed dual boot, the last os install will have the boot (grub) on it. At start-up screen you have the choice to let it start-up as ubuntu or arrow down to "other operating system)..The default can be changed quite easy if you start counting down the kernals on the boot screen starting with 0 to the kernal you want as default start-up.    In the terminal (accesories/terminal/) type gksudo gedit /boot/grub/menu.lst  give your password and change the menu list 'default 0 to what ever number you wanted to boot into. Click save and exit

Here's to not knowing if I installed dual-boot but I will investigate this when I get home (to where my Ubuntu lies in wait) 

I did not receive any discs with the new HP ... no recovery discs or driver discs like my old faithful Gateway laptop with WinXP ... is it possible that Vista is un-erasable from the drive and I just need to know how to get at it?  

:confused: <------------- thought I knew what I was doing ... once a log time ago hahaha

---

### Post by sayakb on 2008-02-26
@OP
If you used the Guided partitioning at the disk partitioner, then unfortunately, you erased your entire disk including the recovery partition. You need a recovery disk to get your vista back. As you are new to Ubuntu, you can either choose to stay with it, or dual boot it with Vista. For dual booting, just ask for some recovery disks from the HP retailers, partition your disk through the recovery disk and leave a 10GB partition for Ubuntu. 
But if you wish to stay with Ubuntu, do nothing!! Just keep posting your doubts and problems (wherever you face any, even the smallest ones), and all the experts here and not-so-experts like me would be glad to help you anytime. :D

Welcome to Ubuntu.

---

### Post by makebusy7 on 2008-02-26
> **LinuxIsInnovation said:**
> @OP
If you used the Guided partitioning at the disk partitioner, then unfortunately, you erased your entire disk including the recovery partition. You need a recovery disk to get your vista back. As you are new to Ubuntu, you can either choose to stay with it, or dual boot it with Vista. For dual booting, just ask for some recovery disks from the HP retailers, partition your disk through the recovery disk and leave a 10GB partition for Ubuntu. 
But if you wish to stay with Ubuntu, do nothing!! Just keep posting your doubts and problems (wherever you face any, even the smallest ones), and all the experts here and not-so-experts like me would be glad to help you anytime. :D

Welcome to Ubuntu.

I am going to call HP and get recovery discs because I feel that I should already have them ... I mean didn't I purchase the OS with the actual machine?  

I will dual-boot because my partner has had just about enough of these computer shenanigans and he needs the MS to work for him.    Grrrrrrr.   :lolflag:

I like Ubuntu.  It's not MS.  It turns on and it turns off.  No boot time.  The internet pages whip past me as I surf.  I feel like I remodeled my bedroom with warm colors ...

---

### Post by guilly on 2008-02-26
I know that sometimes retailers don't provide recovery disc's but instead what they do is they partition yourdrive and on the one partition they install an app which is supposed to re install your OS to factory settings for you. You may want to check it out. Usually the partition is 2-3 GB in size.

---

### Post by sayakb on 2008-02-26
> **makebusy7 said:**
> I am going to call HP and get recovery discs because I feel that I should already have them ... I mean didn't I purchase the OS with the actual machine?

You did have the recovery partition.. You can create your own recovery disks from the partition. :)

---

### Post by Rolcol on 2008-02-26
> **makebusy7 said:**
> I am going to call HP and get recovery discs because I feel that I should already have them ... I mean didn't I purchase the OS with the actual machine?  

I will dual-boot because my partner has had just about enough of these computer shenanigans and he needs the MS to work for him.    Grrrrrrr.   :lolflag:

I like Ubuntu.  It's not MS.  It turns on and it turns off.  No boot time.  The internet pages whip past me as I surf.  I feel like I remodeled my bedroom with warm colors ...
Are you sure it didn't come with a recovery partition instead of the recovery CDs?  You may have deleted that...

---

### Post by makebusy7 on 2008-02-26
> **guilly said:**
> I know that sometimes retailers don't provide recovery disc's but instead what they do is they partition yourdrive and on the one partition they install an app which is supposed to re install your OS to factory settings for you. You may want to check it out. Usually the partition is 2-3 GB in size.

okay then, where does Ubunto show me what's on the disc?  do I need Win Dir Stat or a similar application? 

I really beileve that I deleted it.  :(

---

### Post by Papa-san on 2008-02-26
I deleted the microsoft virus from my machine about two years ago. Learning Ubuntu has been a real challenge, but I continue to persist at learning it. It isn't windows, and the biggest obstacle you face at this time is to stop thinking in windows!!!

Set up your system as a dual boot, and play with the Ubuntu. My wife has been using my laptop for a few months now and really likes it. She isn't interested in learning how to use the terminal, but once I have the thing set up, she LOVES using it. (No wasting time running antivirus software, spyware removal programs, the dreaded 'defrag', etc...)

Stick with it. It is a better way!

---

### Post by brennydoogles on 2008-02-26
I will have to agree with LinuxIsInnovation... chances are you dumped your Vista completely. But, you seem to have a good attitude about Ubuntu (aka, you are willing to give it a chance), and you seem to be more than smart enough to run it. With that said, unless you have some CRAZY hardware issues I'm sure we could get you set up with Ubuntu so that you never look back. With that said, What do you know about your computer hardware? I see that you have a nice processor, and almost enough RAM ( :p ), How about your video card?? If it is an NVidia, then you will have no problems getting awesome Linux drivers. If it is an ATI, it will be a little bit more difficult, but you can still get it running well with a little help from Ubuntuforums. 

Now on to your issue reading your external hard-drive. Just guessing here, but the reason for this is usually that Windows uses an NTFS file system on hard drives by default, which requires a "driver" that isn't pre-installed on Ubuntu, but is easy to get. To get it (and also to install anything else pretty much), go to your main menu (usually on the top bar) and go to System -> Administration -> Software Sources (note, you only have to do this part once, after that, the settings are saved). On the main page, make sure the checkboxes for Universe and Multiverse are checked (this will give you access to a wider selection of software to install, all of which has been checked and is Virus-free). Save your changes and close that window. Now go to System -> Administration -> Synaptic Package Manager. You will come to love this program. It gives you access to THOUSANDS UPON THOUSANDS of free programs to install, everything from fun little games (and a few crappy ones) to utilities that could be used to crack a WEP key on a wireless network, as well as pretty much everything in between. The first thing you need to do is click the reload button at the top. This will make sure that you have access to the newest software. Now press Ctrl + F on your keyboard. This will bring up a search box, and if you are ever looking for a program to do something specific, this is a good way to find it. Search for ntfs-3g. it should be the first program you see. To install it, just click the checkbox next to it, and then "Mark for Installation". After that, you can browse around looking for anything else you want to install, and at the end to install the programs, click apply. They will download and install automagically. For the most part, you won't even have to do anything. Now, to configure your HD, there are two ways to do it, manually or automatically. I recommend manually, because it is a good learning experience (and kinda fun if you are nerdy like me), and it is also more reliable (if you want something done right do it yourself). Unfortunately, I don't have time to type up how, but the forums are FULL of tutorials on how to do it, so if you haven't found out how in a few hours when I get home I will post a link to a tutorial. To do the automatic way, just open Synaptic back up, and search for ntfs. One of the programs will offer to automatically set up any NTFS hard drives, but I can't remember which because I am stuck at a Windows computer at the University right now. I hope this helped!!

---

### Post by guilly on 2008-02-26
> **makebusy7 said:**
> okay then, where does Ubunto show me what's on the disc?  do I need Win Dir Stat or a similar application? 

I really beileve that I deleted it.  :(

Off the top of my head since i'm at work I believe you can check it out in disk utilizer ??(sorry I'm at work and can't quite remember off the top of my head)  it's somewhere under applications if not I know that if you open up a terminal and do an sudo apt-get install gparted. Then once that's installed you can go into adminstration open gparted and it should show you every partition you have on your hard drive.

---

### Post by makebusy7 on 2008-02-26
Wow thanks for all the awesome advice! 

I have an Nvidia video card AND I already got the linux driver for it but I didn't get past the install. 

I am going to do all these things once I get home.  

THANKS AGAIN and please feel free to feed the n00b :)

---

### Post by brennydoogles on 2008-02-26
> **makebusy7 said:**
> Wow thanks for all the awesome advice! 

I have an Nvidia video card AND I already got the linux driver for it but I didn't get past the install. 

I am going to do all these things once I get home.  

THANKS AGAIN and please feel free to feed the n00b :)

If you have an NVidia card, don't bother compiling the driver. Just go to System -> Administration -> Restricted Drivers Manager, and Ubuntu will install it Automagically for you. That's the easiest way.

---

### Post by makebusy7 on 2008-02-26
> **brennydoogles said:**
> If you have an NVidia card, don't bother compiling the driver. Just go to System -> Administration -> Restricted Drivers Manager, and Ubuntu will install it Automagically for you. That's the easiest way.

But I get an error saying "the software source nvida is not enabled" 

I have the driver sitting here on my desktop, I just dont know what to do with it

---

### Post by Flying caveman on 2008-02-26
system>admin>software sources> enter your password  then check the software restricted by copyright box.

Then do what brennydoogles said to do above.

---

### Post by chris.a.barker on 2008-02-26
Another small tidbit of information that usually helps new users out is this:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

You can find basically all of the needed information to get you up and running with the basics. In addition to the page I have mentioned please continue to visit the forums as they are an invaluable resource.

Welcome to Ubuntu!

---

