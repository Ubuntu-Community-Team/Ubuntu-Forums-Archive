---
title: "Remove Ubuntu from Windows 8 machine safely?"
date: 2013-09-09
forum: Any Other OS
---

### Post by mistu on 2013-09-09
Hi,

I hope this is an appropriate place for this thread. I bought this HP Pavillion desktop computer (with Windows 8 preinstalled) back in December. I had been planning on dual-booting with Linux for some time, and just got around to it last month. I ran into all kinds of issues involving UEFI and not being able to boot my live USB, and then after actually getting Ubuntu installed I had issues with Grub not showing up, and once that was resolved and I finally had options to boot into either Ubuntu or Windows, I realized to my dismay that Ubuntu would not boot. Windows booted just fine.

I tried two versions of Ubuntu and one version of Linux Mint (which ate Grub and I had to re-install Ubuntu to get my computer to boot at all.) Now I just have a useless Ubuntu partition that I can't even use sitting on my computer. This has been the biggest headache ever.

I have tried multiple things to get Ubuntu to boot, but I have given up. Windows has won this time, because unfortunately, I've just started college and I need it for school. **So, I want to remove Ubuntu completely from my computer and have the PC boot straight to Windows.**

Now, I understand that what I need to do here is to remove the Ubuntu partition, remove Grub, and then fix the Windows MBR. This would be all fine and dandy up until the part where I have to fix the MBR. I do not have a Windows 8 installation disc as the OS came preinstalled. What I do have is a useless HP recovery partition which only gives me the option to restore my computer to its factory settings, which I do NOT want to do. I can make HP recovery discs, but from my understanding, they do the exact same thing that the partition does, which would be a complete waste of time and resources to make. I suppose my question here is, **can I repair the MBR from within Windows 8?**

If not, is there a simpler way to remove Ubuntu safely so that I don't lose Windows or render my computer unbootable? If I had known I was going to run into so many problems, I wouldn't have tried to dual-boot this computer in the first place.

Sorry for the extremely long post, but I'm hoping someone here knows what I can do to fix the mess I've made. Thanks!

---

### Post by ajgreeny on 2013-09-09
You say "I have tried multiple things to get Ubuntu to boot, but I have given up.  Windows has won this time, because unfortunately, I've just started  college and I need it for school. **So, I want to remove Ubuntu completely from my computer and have the PC boot straight to Windows.**" but I can not find any questions about that which you have posted here, so I wonder if we can figure out why ubuntu will not boot.

Did you install after first running the live system?  It is always worth doing that as you will quickly see if any major hardware problems exist.
Did you follow all the UEFI requirements shown in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to get the system installed? If you didn't go through that I recommend that you read it and then try again when you may be a bit more lucky.

If you really want to remove ubuntu from the machine you will have to restore the windows bootloader, which I am afraid is where I have to bow out, not having used windows since XP.

---

### Post by mistu on 2013-09-09
Hi ajgreeny,

Thanks for your reply. I did run the live system first, after wrestling with it for a while. I couldn't boot the live USB from EFI. When I tried, it would just freeze up at a black screen and I would have to hard reset my PC. In order to get the live USB to boot, I had to go into BIOS and boot it under Legacy, which worked fine. Once I was into the live system, that's when I installed Ubuntu.

Also, I did indeed follow the instructions on the UEFI community page. Disabled FastStartup, disabled Secure Boot (which is required in order to enable Legacy mode), and then I had to run Boot Repair to get Grub to show up at all.

When I try to boot into Ubuntu, I get hung up at the purple screen. It stops trying to boot and just freezes up, similar to what happened when I booted the live USB in EFI mode. I looked through a ton of forum posts with similar problems to this one and tried several solutions listed, but they either didn't work, or I couldn't try them because it required me to boot into Ubuntu in some way.

It would be great if I could get Ubuntu to boot, but like I said, I've given up on trying for now.

---

### Post by s3a on 2013-09-09
Honestly, I didn't read everything you said (:P) but, you should be able to use a live OS to remove the Ubuntu partition(s) and then resize your Windows partition using gparted so that Windows can use all the space of your hard drive and then, if Windows has problems, boot off the Windows disc and click Repair and then use the Windows command line and issue the bootrec /fixmbr and bootrec /fixboot commands.

---

### Post by ajgreeny on 2013-09-09
Did you have the required bios_grub partition in your system.  I believe it is needed if you boot ubuntu in BIOS mode, but if you have windows already in UEFI mode you will need ubuntu also in UEFI mode.

Can I also check if the ubuntu install medium was 64 bit as that is all that you can use if dual booting with Win8, I believe.

---

### Post by oldfred on 2013-09-09
Actually with UEFI, another install does not overwrite a previous install's boot loader like with BIOS and only one MBR on hard drive.
The efi partition is where every system installs its UEFI boot files and each system has a folder. Ubuntu's is in ubuntu and Microsofts is in Microsoft folder.
So from UEFI menu in UEFI mode with secure boot on or off, you should just be able to choose Windows and boot. 
You may have installed Ubuntu in BIOS mode if you turned off UEFI or turned on CSM/BIOS/Legacy mode.

Issue of black screen is not related to UEFI, but you may need proprietary drivers. What model HP.

Other HP that mostly worked with some effort.
 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by mistu on 2013-09-09
Hello again,

s3a - 
I do not have a Windows disc and cannot get to a command line outside of Windows, but thanks anyway.

ajgreeny & oldfred -
First off, the Ubuntu is definitely 64 bit. I made sure of that when I downloaded the ISO. Secondly, I couldn't get my Ubuntu installation media to boot in EFI so I installed it after booting the USB in Legacy mode. However, the first problem I ran into was that Grub didn't show up so I ran Boot Repair and it installed "grub-efi" which got Grub to appear. I guess this means that I didn't install Ubuntu in BIOS mode, and that it is correctly placed in the EFI partition? And if I understood oldfred correctly, this means that I could simply just remove the Ubuntu partition, and all will be well with Windows?

For the purple screen I get stuck at, I read something about drivers being the issue on another forum, but the solution was to boot up Ubuntu in recovery mode. I get the same issue booting it regularly, in recovery mode, or by adding any boot parameters (unless there is one I haven't yet tried).

My PC's model number is p7-1446s.

I will look through the forum posts and see if any of them have anything that could help me. Thanks.

---

### Post by oldfred on 2013-09-09
You installed in legacy mode, but Boot-Repair converted it to UEFI by uninstalling the BIOS grub-pc and installing the UEFI grub-efi.

You should be able to go into UEFI and directly boot Windows. Boot-Repair added correct UEFI chain load entries to the grub menu as grub has a bug and still only creates BIOS type entries that do not work with UEFI.

Many have video issues, what video card/chip does your system have?

---

### Post by mistu on 2013-09-09
Ah, that makes sense.

My video card is AMD Radeon HD 7660D.

---

### Post by oldfred on 2013-09-10
I do not know AMD as I have nVidia. Normally you use nomodeset to get into system with low graphics and install proprietary driver. Your 7000 series is new, so not sure if current AMD driver is best or if you use open source driver.

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)


 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

---

### Post by mistu on 2013-09-10
nomodeset does not work for me. It's one of the first things I tried, but it still hangs at the purple screen. I tried again just to be sure with no luck.

I should probably mention that when I turn Secure Boot back on and boot my computer, I get an error that says "Secure Boot Violation -- Invalid signature detected. Check Secure Boot Policy in Setup." I hit OK, and I get "ERROR: No boot disk has been detected or the disk has failed."

When I select Windows Boot Manager from BIOS under UEFI Boot Sources with Secure Boot off, it still takes me to Grub. When I try with Secure Boot on, I still get the aforementioned error.

---

### Post by oldfred on 2013-09-10
You may have used the Boot-Repair rename function? That is for systems that only boot Windows and you rename grub2's shim to be the Windows file name to boot.

With secure boot only secure boot systems will boot. Ubuntu will install with secure boot but you have to boot installer or Boot-Repair with secure boot on.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

