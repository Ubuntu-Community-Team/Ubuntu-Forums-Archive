---
title: "Successful install but unable to boot on win 8 nor mint? (BOOT-REPAIR)"
date: 2013-04-13
forum: Any Other OS
---

### Post by JaZZyCooL on 2013-04-13
hey guys,
   I just installed my Linuxmint 14 on my windows 8. Using the following steps

1) Created three partitions
```

sda 8 - EXT4 /boot
sda 9 - Swap area
sda10 - EXT4 /

```
2) clicked on the sda 8 and pressed install 
3) After installation opened boot-repair and choose the following options:
```

OS to boot by default - sda10 (Linux now in use)
separate /boot/efi - sda8
separate /boot/partition - sda3 (That is my efi file system for windows 8)

```
4) After this I pressed apply and followed the commands at last pressing forward.
5) After completion, It showed me this message
```

Please do not forget to make BIOS boot on sda3/EFI/Linuxmint/grubx64.efi file!

(I ignored this message because I didn't know what its instructing me to do)

```
6) Now, as told by my friend on this forum, I copied bootmgfw.efi and paste it into my sda8/EFI/Microsoft (I created the folder microsoft)
7) Rebooted my computer

For the first time I was able to boot into Linuxmint, I did nothing and just shutdown my computer started again to test my windows 8. I got the following message
```

error: Can't find command 'drivemap'
error: EFI file path

Press any key to continue...

```
Now I again tried going back to Linuxmint but unable to as soon as I click 'Linuxmint' the screen blacksout and gets stuck where it is.

Can anyone please help me find the solution as I am getting the same problem after 3 installations with continous recoveries. 

```

Here is the summary

https://paste2.org/FV4Xfnsn

```
Your help is highly appreciated.

---

### Post by JaZZyCooL on 2013-04-13
Hey guys, really need help on this on Can you guys please help me out.

---

### Post by oldfred on 2013-04-13
Your link is not working.

But an efi partition is not a /boot partition. An efi partition replaces the MBR as far as function goes with UEFI booting. And each folder for each system in an efi partition is like a different MBR, plus as an efi partition it has more room for code so all of Windows boot loader or grub2's boot loader can fit into the folder. But it does not have the grub menu (normally) nor kernels. 

With Desktop installs you should not need a separate /boot partition. And grub should just install to the existing efi partition.

You can only have one efi partition per hard drive and you use gparted to set efi partition using the boot flag. But boot flag in gpt partitioned drives means something totally different than a boot flag in MBR(msdos) partitioning.

Does Mint even work with secure boot? Some systems will boot Windows with secure boot off (all should) but some have to have secure boot on to boot Windows and Ubuntu has the Microsoft key in grub's shim file.

---

### Post by JaZZyCooL on 2013-04-13
Hey Can you tell me the solution for the same, what should I do sir, because I am really pissed off with this EFI ****. If you can help me out it would great sir.

Your help is highly appreciated.

---

### Post by oldfred on 2013-04-13
If not Ubuntu with the added secure boot capability, I am not sure.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

