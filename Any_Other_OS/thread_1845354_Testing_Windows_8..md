---
title: "Testing Windows 8."
date: 2011-09-16
forum: Any Other OS
---

### Post by MasterNetra on 2011-09-16
Started testing Windows 8 (Developers Preview), just freshed installed it onto my laptop here. I know not usually a good idea to install on your normal machines but most of my crap is stored online or on a backup drive and reinstalling is of little consequence to me these days.

Thus far I am actually enjoying the metro thing I didn't think I would and not really sure why, its just strangely comfortable, to me anyway.

Two big bonuses to me thus far is that I can control brightness on my laptop from install (not the case for win7, some issue with the latest driver for my vid card). And IE here has a spellchecker (about time). Also once logged in it seems to be even more responsive.

Just thought I'd share, going to attempt to install Morrowind later and see how that plays on here.

---

### Post by wojox on 2011-09-16
Sounds cool. I was thinking of downloading a copy myself. Are you running 32 or 64 bit?

---

### Post by kaldor on 2011-09-16
I tried, but it won't boot. I get an error saying the PC needs to be restarted. Might need to change a BIOS setting, but I'll probably just wait until an alpha/beta.

---

### Post by _d_ on 2011-09-16
From what I've read from most people, the best working version is the 64bit w/developer tools.

---

### Post by oldos2er on 2011-09-16
Moved to Other OS/distro talk.

---

### Post by MasterNetra on 2011-09-16
32bit I do have a 64bit processor but with only 1GB of ram 64bit is not even a option. To note though,

1. Only way I've found to quit programs is to use task manager to end them, you can switch from them which seems to "suspend" that app.

2. Flash does not work in the metro display of IE, but is fine in the desktop ran version.

On a side note Win8 thus far idles at around 370 for me which is less then win 7 for me. So a bit of improvement atm, granted MS isn't done implementing features yet so we'll see where that goes.

---

### Post by ManualSparrow on 2011-09-17
I am running the 64-bit non-developer version (the one that fits on a standard DVD) and it works fairly well.

So far the experience has been comparable to the next-gen Linux UIs (Gnome Shell/Unity), in that the "launchpad" is accessible via the Super key or screen corner and brings up an interactive list of apps that narrows as you type. Also, boot time has been extraordinarily improved (on my 5400rpm drive, we're talking maybe 15 seconds from BIOS to home screen, and then you're actually ready to go, unlike in previous releases). 

Also, has anyone tried reinstalling GRUB after Windows 8 wiped it? I have heard GRUB will not be able to find the new Protogon FS, which would render Windows 8 unbootable. As far as workarounds go, I suppose installing GRUB on a flash drive then updating the grub.conf file with sda partitions would work. Thoughts?

---

### Post by tjeremiah on 2011-09-17
I installed it on my laptop too, 64bit version. It runs very smooth and after using it for about 2 days now (?), switching back and forth from desktop to metro ui isnt that much annoying anymore.

---

### Post by el_koraco on 2011-09-17
> **ManualSparrow said:**
> 
Also, has anyone tried reinstalling GRUB after Windows 8 wiped it? I have heard GRUB will not be able to find the new Paragon FS, which would render Windows 8 unbootable. As far as workarounds go, I suppose installing GRUB on a flash drive then updating the grub.conf file with sda partitions would work. Thoughts?

Or you can let the Windows bootloader take over the boot sequence and not worry about further updates borking GRUB.

---

### Post by shuttleworthwannabe on 2011-09-17
Well, did anyone mention that boot sequence is fast and loads login screen in just over 20 secs on my laptop (emachines D620 1.6GHz AMD Athlon, ATI Radeon X1250, 4GB DDR2 RAM @800MHz) . This is note without any large programs added to the stock first install. I will monitor this as I install more apps and programs (Office, etc) and get the registry bloated with use).

I am amazed.

---

### Post by _d_ on 2011-09-17
Well since I have nothing to do today, and I don't have much currently on my Windows7/Ubuntu partitions as far as data...

Decided to redownload Windows 8 dev preview, burn it to DVD and actually install it on some real hardware which being my desktop.

It's gonna be fun on a bun!

---

### Post by ManualSparrow on 2011-09-17
> **el_koraco said:**
> Or you can let the Windows bootloader take over the boot sequence and not worry about further updates borking GRUB.

But the Windows boot loader doesn't recognize Linux, so you need another one somewhere along the line if you want to use a single hard drive.

---

### Post by Mitjaa on 2011-09-18
Awesome! How much ram does win 8 need?

---

### Post by _d_ on 2011-09-18
> **Mitjaa said:**
> Awesome! How much ram does win 8 need?

[IMG]http://i53.tinypic.com/sqqn0p.png[/IMG]

That is my current idle usage after closing down most of my apps. Granted I still have more things running than I did on Windows 7, it just about sits even with 7 as far as RAM usage goes.

---

### Post by MasterNetra on 2011-09-19
> **_d_ said:**
> [IMG]http://i53.tinypic.com/sqqn0p.png[/IMG]

That is my current idle usage after closing down most of my apps. Granted I still have more things running than I did on Windows 7, it just about sits even with 7 as far as RAM usage goes.

That's for the 64bit. 32bit, I wouldn't recommended going below 1GB, could fudge it with 768, but wouldn't be able to do too much.

---

### Post by guitar_man on 2011-09-20
where can I download the iso?

---

### Post by GWBouge on 2011-09-20
[http://msdn.microsoft.com/en-us/windows/apps/br229516]("http://msdn.microsoft.com/en-us/windows/apps/br229516")

---

### Post by el_koraco on 2011-09-20
> **ManualSparrow said:**
> But the Windows boot loader doesn't recognize Linux, so you need another one somewhere along the line if you want to use a single hard drive.

You can just chainload to from BOOTMGR, with GRUB residing on /. I don't actually know the procedure, since I don't use Windows, but I wouldn't setup a dual boot with GRUB eating up the MBR, there's just way too many associated bugs.

---

### Post by altimax98 on 2011-09-20
I enjoy it a lot. I have a x64 build with 4gb of ram and a triple core AMD processor oc'd and it runs so much faster then windows 7. Its real snappy... Although after prolonged use it will get a irq error, almost repeatedly after a few hours of use. It is quite stable and hopefully it is a sign of better things to come.

also windows 8 x64 won't install at lower then 2gb ram ;-)

---

### Post by oscarivera9 on 2011-09-21
> **ManualSparrow said:**
> I am running the 64-bit non-developer version (the one that fits on a standard DVD) and it works fairly well.

Also, has anyone tried reinstalling GRUB after Windows 8 wiped it? I have heard GRUB will not be able to find the new Protogon FS, which would render Windows 8 unbootable. As far as workarounds go, I suppose installing GRUB on a flash drive then updating the grub.conf file with sda partitions would work. Thoughts?

I downloaded the 64 bit non-developer about 5 days ago but I've been so busy I haven't had the time to install it.  Thank God, because now I hear about this GRUB problem!
[SIZE=2]
[/SIZE][FONT=Microsoft Sans Serif][SIZE=2]Does anyone know any more about it?  How does GRUB2 interact with Windows 8?[/SIZE][/FONT]  Microsoft should just accept that Linux exists once and for all.  

I've been debating installing Windows 8 on Virtual Box or on a real partition, so it seems like I may need to do it on Virtual Box.  The only problem with using Virtual Box is that it's suggested in the Microsoft website that you use about 20 GB for a 64-bit install and something like 16 GB for the 32-bit, and you have to use the version that your host system runs, which in my case is 64-bit.  In my opinion that's a hefty size for a basic (without any programs) installation in a virtual environment.

---

### Post by BrokenKingpin on 2011-09-21
Personally I have no patients for Windows these days. Instead of focusing on new user features they should spend some time fixing the fundamental flaws in the OS (I realize this is easier said then done). 

The way Windows handles updates is completely broken... I did a fresh install of Windows Vista for a friend and it took about 4 hours and 11 reboots just to bring the OS up to date (Win 7 is no different). On Linux or BSD it would just be one round of updates and one reboot (and the reboot is only needed for a kernel or Xorg update).

I know every OS is going to have issues, but Windows has had the same flaws since windows 95. Everyone says that Win 7 was a huge step forward, but I really don't get what everyone is going on about. Sure it runs a little faster the Vista, but I honestly don't see much of a difference. Ubuntu offers a lot more features out of the box, and uses far less resources.

As far is Win 8 goes, I can't say I like the new interface at all from what I have seen. Sure, it might be okay for a tablet, but they have a lot of work to slim down the rest of the OS to be any good on mobile devices.

---

### Post by alegomaster on 2011-09-21
I find windows 8 to be horrible so far compared to windows 7. All of the UI changes was making me feel sick. Plus it cannot work with GRUB, so I had to reinstall it to be able to access my linux partition.

Microsoft, Microsoft, Microsoft: let me revert to windows 7 mode with windows 8, or name windows 8 : windows tablet.

---

### Post by oscarivera9 on 2011-09-22
> **alegomaster said:**
> I find windows 8 to be horrible so far compared to windows 7. All of the UI changes was making me feel sick. Plus it cannot work with GRUB, so I had to reinstall it to be able to access my linux partition.

Microsoft, Microsoft, Microsoft: let me revert to windows 7 mode with windows 8, or name windows 8 : windows tablet.

This is the second time I hear of someone saying Windows 8 doesn't work with GRUB.  What has been other  people's experience?
I used Virtual Box last night to install Windows 8 with the sole purpose of finding out what the deal is with GRUB.  Later on today I will be installing Debian 6 to find out what the problem is and if there is a way to work around it.

---

