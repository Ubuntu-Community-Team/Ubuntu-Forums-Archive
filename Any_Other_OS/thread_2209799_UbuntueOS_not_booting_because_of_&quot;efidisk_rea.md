---
title: "Ubuntu/eOS not booting because of &quot;efidisk read error&quot;."
date: 2014-03-07
forum: Any Other OS
---

### Post by anything else really on 2014-03-07
Hello Ubuntu Community, 
first of let me introduce myself to you.
I am a newbie at Linux, but I just love overall the Linux Distros, I can't really say why, maybe because I kinda hate Windows, maybe because I love Open Source Projects where you can learn something however yesterday I was brave enough to install elementaryOS (dualBoot it with Windows8), it was kinda a hell to find out how to install it on a pre-installed Windows 8 Laptop. However yesterday it worked perfectly, nothing wrong everything expected as planned :D, though I couldn't start Windows because of some error called "command 'drive not found" or something similiar, however I looked over at Google and the UbuntuForums and found out that I should probably install Boot-Repair and repair "common errors", however I did everything as it was instructed to me, then Windows 8 could start, but Elementary OS couldn't. It said for like 1-2 seconds something about "efidisk read error", and immidatley went to GNU Grub or something like that (somehow looked like a Terminal without and interface). However I am not able to boot into elementaryOS, but Windows 8 works perfectly, any suggestions?
thank you!
The pastebin btw, [http://paste.ubuntu.com/7050506/](http://paste.ubuntu.com/7050506/) , something to do with Grub I guess?

---

### Post by phidia on 2014-03-07
I'm taking a guess here but maybe UEFI is causing issues? See [the guide here]("https://help.ubuntu.com/community/UEFI") and hopefully that helps.

---

### Post by anything else really on 2014-03-07
Does that mean I have to reinstall eOS?

---

### Post by howefield on 2014-03-07
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by oldfred on 2014-03-07
It looks like you originally installed in BIOS boot mode. 
UEFI & BIOS are not compatible and you can then only dual boot by directly booting from UEFI menu not from grub. 
But it looks like Boot-Repair converted install to UEFI boot.
But you have the older version of grub2's os-prober that does not create correct UEFI boot entries. It still creates BIOS boot entries that will never work.
Boot-Repair has created correct UEFI chain load entries to Windows, so use those new entries.
Use this or boot from UEFI menu:
menuentry "Windows UEFI bootmgfw.efi"

Do not turn on secure boot nor hibernation(fast boot) in Windows.

---

### Post by anything else really on 2014-03-08
Thank you for your answere, though I don't want to make any mistakes, so could you possibly give me a step-by-step instruction?
Thank you!

---

### Post by oldfred on 2014-03-08
Can you boot from UEFI/BIOS? You should have options for both Windows and ubuntu.

And the Ubuntu option should give you a grub menu with Ubuntu and several Windows options. But only some of the Windows options will work.

---

### Post by anything else really on 2014-03-08
Yes, I can boot from Bios (if you mean by spaming esc to get onto bootloader) however oi I choose eOS something similar like a terminal pops up and I can give commands such as exit,boot,etc. If i write boot it says it can't find a kernel.

---

### Post by oldfred on 2014-03-08
That sounds more like you are getting to grub menu not UEFI menu. UEFI is before grub.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)



Several have posted their screens.

---

### Post by anything else really on 2014-03-08
Well mine looks like the third one of you attached Thumbnails, but as I said if I click on "ubuntu" / "elementaryOS" the terminal of GRUB will start, and if I write "boot" into it or "continue" elementaryOS will start and tell me that it didn't find any kernel

---

### Post by oldfred on 2014-03-08
Are you still booting with the BIOS mode as when converted to UEFI, the BIOS mode will give those type of errors as it is not really configured correctly, but may manually boot.

If in UEFI mode, do you get a grub menu?

---

### Post by anything else really on 2014-03-08
So I just made photos of it so you might imagine more of it :), thank you for staying on this thread for so long so far :)!

---

### Post by oldfred on 2014-03-08
CSM is BIOS boot. You want UEFI boot so try changing CSM to disabled.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 


But I think you may still be booting in UEFI mode? Some systems boot either way depending on settings. 

Does Windows boot or do you get grub from Windows boot entry?

---

### Post by anything else really on 2014-03-09
windows boots because I changed the boot priority, even though grub doesn't even start anymore except sometging like in picture 2 and 3. also i tried to disable CSM, but it won't help either.

---

### Post by oldfred on 2014-03-09
Try Boot-Repair again to re-install grub. Be sure to boot in UEFI mode and reinstall grub in efi.

If Boot-Repair offers a 'buggy' UEFI fix say no. That is only for computers that do not boot an ubuntu entry from UEFI. Some vendors modify UEFI to only boot the Windows entry.

---

### Post by anything else really on 2014-03-09
If I am in UEFI mode, how can I repair it then in EFI mode?

---

### Post by oldfred on 2014-03-09
You boot in either UEFI or BIOS from live installer. Or is your Ubuntu is working you can boot in UEFI mode from hard drive. Just do not boot in BIOS mode from any device.
UEFI menu should show the two boot options.

From live DVD or flash drive, you get grub menu if in UEFI mode or accessiblity screen with BIOS.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by anything else really on 2014-03-10
Still not working, [http://paste.ubuntu.com/7067255](http://paste.ubuntu.com/7067255)

---

### Post by oldfred on 2014-03-10
Boot-Repair shows this extract from your UEFI. Can you boot both Windows and Elementary?
>  BootOrder: 0000,0002,0003
Boot0002* Windows Boot Manager
Boot0003* UEFI: Sony Storage Media 1.00
Boot0000* elementary



 This entry added by Boot-Repair in grub menu should boot Windows also.
menuentry "Windows UEFI bootmgfw.efi" 
This entry from the buggy os-prober will not work. New versions of grub in 13.10 fixed this bug.
menuentry "Windows 8 (loader) (on /dev/sda4)"

---

### Post by anything else really on 2014-03-10
I can only boot Windows, which is fine. But if I try to boot eOS it says "Kernel not found", which shouldn't be true, because it worked perfectly before I repaired the problem with Windows. Since I used Boot Repair to fix the Windows bug where it won't boot, I got that problem with that Kernel.

---

### Post by oldfred on 2014-03-10
Is that error after grub menu or before. Or is it UEFI error or grub/boot error?
If you have grub menu can you boot recovery mode or second kernel?

---

### Post by anything else really on 2014-03-10
Made a short video which is better to explain I guess, [https://www.youtube.com/watch?v=HQNdrOoUCoA&feature=youtube_gdata_player](https://www.youtube.com/watch?v=HQNdrOoUCoA&feature=youtube_gdata_player)

---

### Post by oldfred on 2014-03-10
Oh, you have 
grub>
Which is that grub is not correctly installed. You should get that is booting in BIOS/Legacy/CSM mode as now your grub is in UEFI boot mode. 

If booting in UEFI mode and getting that I would use Boot-Repair to reinstall grub in efi boot mode.

---

### Post by mccalleyt on 2014-03-11
Well I know on my ASUS X501A Laptop I had to go into the BIOS and turn off secure boot. That could be a potential problem. I don't remember exactly what the errors were but I think they were very similar. Mine was called secure boot I guess yours maybe CSM but I would check either way.

Thanks,
mccalleyt

I think you may have to reinstall to fix the issue. Only in part because it would be easier than going thru the pain staking step to reinstall grub2 and fix the configuration.

---

### Post by anything else really on 2014-03-11
@Oldfred, I already re-installed GRUB by booting eOS in UEFI Mode with my USB Stick (clicked on "Try eOS") then install BootRepair and repair it, didn't work though.
@mccalleyt Secure Boot is off, aswell CSM (There are actually 2 things, CSM and Secure boot, both disabled, still not working).

---

### Post by oldfred on 2014-03-11
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by anything else really on 2014-03-11
[http://paste.ubuntu.com/7075800/](http://paste.ubuntu.com/7075800/)

---

### Post by oldfred on 2014-03-11
I do not see anything, other than the extra grub in the MBR that would give that type of error if booting in BIOS mode not UEFI.
Otherwise something with your version is not correct.

---

### Post by anything else really on 2014-03-12
I guess I will try to format the Volume on which eOS is, and try to install Ubuntu. Just not sure which one as Ubuntu 13.X does support it untill 2015 (I think) and the 12.X longer, so can you suggest me which one I shall install?

---

### Post by oldfred on 2014-03-12
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Either 12.04.4 or 13.10.
In April 14.04 will be out. If your system is Haswell based, then this may work, but should not be installed as main working system until released. Those testing it find Haswell systems work better with it, but also have other installs.
Both 12.04 & 14.04 are long term releases.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by anything else really on 2014-03-12
This is kinda funny now, after I installed Ubuntu 12.04 my Wlan om Ubuntu won't work. It tells me I deactivated it with the hardware-hotkeys but if I try to turn them on, it won't work. Neither will it on "Settings>Network".

0: asus-wlan: Wireless LAN
Soft blocked: no
Hard blocked: no

1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes

Ubuntu and Windows works fine btw, so thank you

---

### Post by oldfred on 2014-03-12
I do not know if any of these are close enough to your model to be similar. Often UEFI or BIOS is similar by vendor.
And they may discuss issues resolved or not somewhere in thread.

 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

