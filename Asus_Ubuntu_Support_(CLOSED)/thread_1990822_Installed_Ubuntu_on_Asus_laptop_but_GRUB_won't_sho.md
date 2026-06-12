---
title: "Installed Ubuntu on Asus laptop but GRUB won't show up"
date: 2012-05-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by KidFlash1904 on 2012-05-29
Like the title says, I installed 12.04 64 bit on my laptop:

Asus G75VW
Intel Ivy Bridge i7
16 GB ram
Geforce GTX 660M

It said to restart the computer after it was installed, and I did expecting GRUB to show up but it just skipped right to Windows 7. Anyone knows what's going on?

---

### Post by oldfred on 2012-05-29
Did you install in UEFI or BIOS mode. Or did you install one in UEFI and the other in BIOS. They must both be the same to both work.

Post link from this:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by KidFlash1904 on 2012-05-30
Thanks for the reply,  oldfred.

I'm not really sure, I wasn't even aware that there was UEFI in my computer. But here's the link from the 'Create BootInfo' option, I don't want to do something incorrect: [http://paste.ubuntu.com/1014206/](http://paste.ubuntu.com/1014206/)

---

### Post by oldfred on 2012-05-30
You have gpt partitioning and Windows only boots from gpt in UEFI mode. Windows can be installed in MBR mode with BIOS.

Your Ubuntu installed in BIOS mode not UEFI. Not sure if in UEFI/BIOS you can choose which way to boot or not. Some early UEFI seemed to just look for the efi partition and if not efi files found, default to BIOS and look in MBR for boot code. Some now report a switch in the BIOS/UEFI menu for method to boot.

There was a bug in the Ubuntu installer that reformated the efi partition, I think it has been fixed but back up efi partition anyway.

From the UEFI menu you should see two boot choices on the Ubuntu liveCD or USB, one is UEFI or efi and the other is BIOS, legacy, AHCI or other term.  If you boot installer in efi mode, it then should install in efi mode. You should now use Sometime else or manual install to choose to reuse existing partitions.

---

### Post by KidFlash1904 on 2012-05-30
Here are some images from the boot up menu so you can see what I'm  working with here:  

[IMG]http://i209.photobucket.com/albums/bb271/younglink51423/2012-05-30_12-18-26_799.jpg[/IMG]  

[IMG]http://i209.photobucket.com/albums/bb271/younglink51423/2012-05-30_12-18-41_85.jpg[/IMG]  

[IMG]http://i209.photobucket.com/albums/bb271/younglink51423/2012-05-30_12-18-53_134.jpg[/IMG] 

[IMG]http://i209.photobucket.com/albums/bb271/younglink51423/2012-05-30_12-19-12_155.jpg[/IMG]

I  disabled UEFI boot in the 3rd image and it just skipped straight to  Windows again. It was on enabled by default. Then in the last image I  tried to launch EFI Shell but it said 'Not found!'.   

How do I back up the efi partition? Sorry for all the questions but I'm  new to this BIOS and UEFI stuff since my last laptop just had BIOS.

---

### Post by oldfred on 2012-05-30
Better to use smaller pictures and upload using the paperclip icon in the full message edit panel.

You need to leave UEFI on or you will not be able to boot Windows. And you want it on to correctly install Ubuntu.

You should be able to use the Ubuntu liveCD to just copy the efi or sda1 partition. It should not be large as it really only has the Windows efi loader in it now. You can copy to flash drive or other external device.

Some have said they installed Ubuntu in BIOS mode and added the grub efi boot loader to the efi partition and somehow made it work. Not sure of details. I think you would have to use the new boot option in your UEFI menu.

Someone posted this from a different UEFI, but like your add new boot option. This would be after getting grubx64.efi installed from the Ubuntu liveCD.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


You have to boot Ubuntu liveCD in UEFI mode. Is that the launch EFI shell or boot option #2 which seems to be other devices?

Boot repair is UEFI aware, does it offer to reinstall grub2 in efi mode?

---

### Post by c_inconnu on 2012-06-20
have you managed to install your dual boot ? if not, I can help.
if you did, are your FN keys working with ubuntu ?
thanks

---

### Post by Kainous on 2012-07-31
> **c_inconnu said:**
> have you managed to install your dual boot ? if not, I can help.
if you did, are your FN keys working with ubuntu ?
thanks

Hey, another person with problems too.

I followed the steps oldfred posted and wasn't able to get GRUB to load. I also tried boot-repair and it said it intalled GRUB in EFI mode but GRUB still didn't show up.

c_inconnu, you said you can help out?

---

### Post by oldfred on 2012-07-31
See post #2 and post link from BootRepair's BootInfo.

---

### Post by Kainous on 2012-07-31
> **oldfred said:**
> See post #2 and post link from BootRepair's BootInfo.

Here you go:
[http://paste.ubuntu.com/1122639/](http://paste.ubuntu.com/1122639/)

Just to give more information:
I tried the ubuntu liveCD at first, but couldn't boot from it. So I used the alternate version to install, and I can't use that as a liveCD (or at least I wasn't able to get to that option).

Linux Mint 13 Cinnamon LiveCD is bootable for me and that's what I used to get the BootInfo report. I'm trying to install Linux and GRUB on to /deb/sdb/

---

### Post by oldfred on 2012-07-31
@Kainous
You have a UEFI system but installed Ubuntu in BIOS mode. When you boot from the UEFI menu, you should see two options to boot the installer from. One is UEFI and the other is BIOS/legacy/AHCI or whatever your UEFI calls it. Since Windows is in UEFI mode, you should also install Ubuntu in UEFI mode.

Not sure about alternative installer. If you have issues with liveCD did you boot in UEFI mode, and you may also need nomodeset or other boot options to boot. Have not seen anyone use alternative with UEFI.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You may be able to repair install, but it is a bit advanced. May be easier just to reinstall. You have to add the efi partition to fstab, copy grub.efi boot files into the efi partition and maybe some more issues. Boot repair will correctly add a Windows boot stanza as grub2 os-prober does not work correctly with UEFI, yet.

Some threads with users who did install with UEFI.

UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
(Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

---

### Post by Kainous on 2012-08-01
@oldfred

Apparently, UEFI booting was disabled in my BIOS. I enabled it and booted in UEFI mode, but all I get is striped colored bars. I don't think my graphics driver is supported. I'll give the alternative version another go.

---

### Post by c_inconnu on 2012-08-01
I installed windows alongside ubuntu 12.04, here's what I did:

[LIST]
[*]installed W7 _**with UEFI**_ from a W7 Home CD
[*]installed drivers from the bundled Asus CD
[*]installed W7 SP1 downloaded from MS site
[*]installed W7 updates using Windows Update
[*]installed Asus updated drivers using Asus Update
[*]installed Ubuntu 12.04 booting from the install CD _**with UEFI**_
[/LIST]

When ubuntu asked where to put the boot loader, your answer does _NOT_ matter.

To switch betwwen windows and ubuntu, I have to enter the bios and select the OS from the last screen (no grub menu)

---

### Post by oldfred on 2012-08-01
@c_inconnu
You should get a Windows entry in grub's menu with this, but it is not correct curently.
sudo update-grub
The Boot-Repair now has a new feature to add a correct UEFI chainload boot entry.

@Kainous
What video card/chip?
Often video issues are solved with a nomodeset on installer boot & first boot after install until the proprietary drivers are installed. 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Kainous on 2012-08-01
@oldfred

Nvidia GeForce GTX 670M, I'll give your suggestion a try now.

================
Edit 1:
================

Alright, using nomodeset has successfully  allowed me to boot in UEFI mode, installed, and now GRUB boots in UEFI mode properly. It however, points to a wrong path for Win7 booting but I can just use UEFI to boot using Win7's boot manager (Or maybe fix the path later).

Thank you very much for your help oldfred, I'm grateful.

---

### Post by oldfred on 2012-08-01
There is a bug on the boot stanza it creates. It is just a standard BIOS version, not a efi one.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)

Boot-Repair now has a way. Or you can manually add this to 40_custom.

```
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)

#Add menu entry to 40_custom,

gksudo gedit /etc/grub.d/40_custom

#update grub menu
sudo update-grub

You can add your results to the bug. They prioritize on how many users have the issue. So far only 4, so it needs more to report to get any priority. But you have to create another log-in in launchpad.

---

