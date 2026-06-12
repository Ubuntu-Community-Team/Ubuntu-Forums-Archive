---
title: "LiveUSB not working properly/Dual Boot issues"
date: 2013-11-18
forum: Any Other OS
---

### Post by Skunkfoot on 2013-11-18
So I created a LiveUSB of Mint 15. When I go into boot options to boot from USB, it takes me to this screen:

```

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>
```

The only way I've found to actually boot the LiveUSB from here is to run this code: (although obviously I'm new to all this, so I'm not sure what it all does exactly)

```

set root=(hd1,msdos1)
set prefix=(hd1,msdos1)/boot/grub/x86_64-efi
insmod linux
linux /caspervmlinuz file=/preseed/mint.seed boot=casper
initrd /casper/initrd.lz
boot

```

After running that, the LiveUSB boots up into Mint just fine. So then, I go to install Mint alongside Windows so that I can dual boot. I go through the installer, set aside 50 GB or so for Mint, and let it do its thing. Installer completes with no errors. However, even though Mint is now installed on my HD, I'm unable to or unsure of how to boot up into it. There's no grub when I boot up; It just boots up straight into Windows. I know that it's installed on my HD, though, because now I have a new drive that I can see in Windows, but can't access, and when I boot up into the Mint LiveUSB that I created and look at it in GParted, that drive is ext4 and has a swap partition as well (and is the right size). So Mint is there, but I don't know how to get to it.

So I do some research and find instructions on how to repair/restore grub (found here: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UoonU-IUF2w]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UoonU-IUF2w") 

I follow these instructions and everything seems to work fine, but I still have no grub bootloader and no way of booting up into my Mint partition.

Just some more info that might help you help me:

I just watched a buddy create a LiveUSB of Kali and boot up into Kali Live just fine, just like you would expect. I plug that same exact flash drive into my PC, and it doesn't even show up in my boot options. This same thing has happened to me with other LiveUSB's that I've tried to create (Kali, Puppy, etc.)

I've also read that disabling Secure Boot in BIOS and disabling FastBoot will sometimes solve this problem, but I've done both of those things and it hasn't changed anything.

So anyway, my problems are that, for whatever reason, I have no way of booting into my Mint drive, and LiveUSB's don't work properly (if they work at all). Not sure if those two things are related or not.

Any help would be much appreciated. Again, I'm new to this, so if I'm missing something obvious, then I'm sorry for wasting your time, but as of now, I'm pretty much at a dead end and don't really know how else to proceed. 

Thanks again for taking the time to try to help me out!

--Skunkfoot

---

### Post by oldfred on 2013-11-18
Thread moved to Other OS/Distro Support. Since it is the Minty flavor version.

    
The only time you get grub from live installer is if booting in UEFI mode. And Ubuntu has the license for secure boot with the Microsoft key but not sure if Mint does also? But I would expect it to boot in non-secure mode. Perhaps not fully configured for UEFI boot?

You may have to go into UEFI menu and choose the ubuntu or mint entry. 
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Skunkfoot on 2013-11-18
Fair enough, sorry for posting in the wrong section!

Anyway, here's a link to the Boot-Info:
[http://paste.ubuntu.com/6438417/]("http://paste.ubuntu.com/6438417/")

Thanks for the help!

--Skunkfoot

---

### Post by oldfred on 2013-11-18
Not sure why Boot-Repair says your UEFI is not standard. But most vendors are not truly standard.
 Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Is your UEFI from HP the most current version?

Is this an Ultrabook. It seems a bit odd that main drive appears as sdc. Or do you have two flash drives plugged in and they are promoted to sda & sdb?
Ultrabooks have a small SSD that often interferes with install or correct install of grub as SSD uses Intel SRT with RAID and then grub would want to install inside RAID when it should not.

You have these:
/EFI/linuxmint/grubx64.efi 
 /EFI/linuxmint/shimx64.efi

You should find in UEFI menu a linuxmint entry and that will boot grub.
But you have the older version of grub2 which still has the bug on BIOS boot entries which do not work with UEFI. Boot-Repair can add correct entrie or you can manually add it as shown in bug report. If you run Boot-Repair it will add all the HP .efi files as boot entries making a very busy grub. You can edit out entries. Info on that is in link in my signature.

      grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Some UEFI will not directly boot anything but the Windows efi file. For those type systems Boot-Repair will rename the Windows file to be grub2's shim and then UEFI thinks it is booting Windows but is booting grub. And then from grub menu you can boot the backed up Windows efi file. But if you can directly boot mint from UEFI menu best not to let Boot-Repair rename files as then you cannot directly boot Windows from UEFI menu.

---

### Post by Skunkfoot on 2013-11-18
I played around with the Boot-Repair settings and got it to work! I'm now able to get to a grub menu and boot up Mint by navigating through my boot options menu. You were very helpful, and I'm not sure I could've figured it out without you. 

Thanks a lot, oldfred!

--Skunkfoot

---

### Post by oldfred on 2013-11-18
Glad you got it working. :)

---

