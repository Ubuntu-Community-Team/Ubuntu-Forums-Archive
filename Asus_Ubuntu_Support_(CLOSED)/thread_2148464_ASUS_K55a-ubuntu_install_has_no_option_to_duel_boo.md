---
title: "ASUS K55a-ubuntu install has no option to duel boot with Windows 8"
date: 2013-05-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by sgcsg1313 on 2013-05-25
I have a ASUS K55a that im trying to duel boot with Windows 8 and Ubuntu 13.4. Ubuntu will boot just fine off the flash drive into ubuntu with the whole UEFI BIOS crap. I disabled secure boot thinking it would save me the headache but i guess not. 

My problem is that when i get to the point of selection of how I want to install Ubuntu it doesnt give option to select install along side Windows. I tried selecting "something else" but all that does is take me to a partitioning page that shows my 500GB drive has no partitions. Which is not true since I restarted the computer and it booted in to Windows so I know there is a partition on it. I also booted ubuntu from flash drive and was able to mount the Windows OS and see all my files. So that tells me the installer should see the Windows Partition. 

I've been working with this issue for 4 months now. The first time I did get ubuntu to install (not sure how I was able to get that to work with duel booting) but when Windows did its update (Windows updates), it knocked out the ubuntu boot loader and I had to use super grub disk to get back into linux every time, so i just wiped the computer clean and started again with fresh install of Windows.

With all that said, is there something I'm missing here? Yes I did make a UEFI flash drive of ubuntu so thats not the problem (I ened up rebuilding it to make sure I made it UEFI compatible.)

I would post some screen shots but Ubuntu forums will not let me since I'm "new" to the forums.
And yes, i did search the forums for my particular issue, all of them that I have found so far are not exact to my issue. I did look at these instructions without success.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I dont have the option to disable QuickBoot/FastBoot, Intel Smart Response Technology (SRT) or disable FastStartup in the BIOS. But I do have disable secure boot which I disabled before I installed Windows fresh.

Any help on this would be greatly Appreciated.

P.S. I would also like to add that I used a program called "Windows 7 USB DVD Download Tool" to make the Windows 8 Flash Drive incase anyone wanted to know how I made the flash drive

---

### Post by 2F4U on 2013-05-25
Maybe this provides some help:

[http://ubuntuforums.org/showthread.php?t=2078013](http://ubuntuforums.org/showthread.php?t=2078013)
[http://ubuntuforums.org/showthread.php?t=2126265](http://ubuntuforums.org/showthread.php?t=2126265)

---

### Post by sgcsg1313 on 2013-05-25
Thanks :) I will look at these links and hopefully get this issue resolved

---

### Post by sgcsg1313 on 2013-05-26
This issues is going to have to wait until i solve my new issue with windows. Im getting the pc needs to be repaired crap. Until I fix this, i cant proceed to fix the ubuntu issues. So for now I will see if I can close this post and maybe repost at a later date if I get this issue fixed. Even loading the origional image I made of the whole hard drive before booting it for the first time will continue to show this message:
Recovery
Your PC needs to be repaired
A required device isn't connected or can't be accessed.
Error code: 0xc0000225
[ A text saying I should use recovery tools on my installation media to fix the issue. ]
Press Enter to try again 
Press F8 for Start-up Settings
Press Esc for UEFI Firmware Settings

(edit 5/30/2013) Just found out its a hardware related issue with this machine. Its been sent to manufacturer for repair. Once I get the machine back I will attempt to duel boot Windows 8 and Ubuntu

---

