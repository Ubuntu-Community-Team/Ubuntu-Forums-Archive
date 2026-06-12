---
title: "Fixing Bootloader"
date: 2013-09-15
forum: Any Other OS
---

### Post by ShooblaGoo on 2013-09-15
Hello,

I recently attempted to install archlinux but ran into many driver problems, now I wish to go back into windows. However, it seems like I severely messed up the bootloader. I have downloaded Boot-Repair-Disk but it still does not go into windows!
I am desperate for help, thank you.

Here is the output boot-repair gave me:
[http://paste.ubuntu.com/6111365](http://paste.ubuntu.com/6111365)

Edit: I do not have a windows repair CD to fix the MBR.

---

### Post by CeejRab on 2013-09-15
Hello Shooblagoo,

I recently attempted to help someone else with this same issue, here is the post i made for them:

________________________________________________________________________________________________________________________
Youre in a pickle eh? Yikes. I did the same thing believe it or not! But  good news for you is that i can help (i hope!), whereas i didnt have  anyone to help me! 

First off, as said before, dont panic, its ok! Linux is your friend, i  actually switched from windows 7 to ubuntu 12.04 LTS because after using  it for a recovery i fell in love and its so much better than windows.  But anyway im not a salesman... Especially for freeware like linux,  haha. 

Ok so your main goal is to restore your windows 8. To do this you need  to remove grub and fix the windows MBR (Master Boot Record) and windows  boot loader. This will allow you to boot your windows partition and  operating system. To do this, linux is your best buddy! 

Step 1: Hold the Control Key, the ALT key, and press the "T" key. This  will open a new terminal window. If this is too difficult, just press  the windows button on your computer keyboard and type "terminal" in the  search bar that pops up. Once terminal opens, type the following command  in step 2 (without quotes) 

Step 2: in terminal, type "sudo apt-get update" and press enter

Step 3: type "sudo apt-get install -y Lilo"

Step 4: if a prompt comes up, just press enter or click OK

Step 5: type "sudo fdisk -l" to see your partitions. Now, choose the  partition that windows is on and see what it's called. If you have a  SATA HD the main drive should be "sda". All partitions of that drive  will be "sda1" "sda2" and so on, because the numbers represent the  partition. If your drive shows as "sdb" or "sdc", use that instead of  "sda". We want the main hard drive to get its boot loader fixed, so in  the next step you don't need to type the partition number, just the main  drive location (sda, sdb, or whatever your drive is called.)

Step 6: type "sudo lilo -M /dev/sda mbr" (replace the "sda" part with  whatever your drive is called as stated before. If it is "sda" then  leave it that way in the command. Press enter. 

This should be it, just type "exit" in the terminal window and it will  close. Then reboot your computer from the main HD and it should boot  windows normally. If this doesnt work, you can try the less friendly and  descriptive approach which i derived this method from at the following  website [here]("http://thenewtech.tv/how-to/use-ubuntu-and-lilo-to-restore-the-windows-mbr"). 

I hope this works for you, and i trust this was somewhat of a help! Keep calm and linux on!
________________________________________________________________________________________________________________


Here is the link to the thread where i submitted this advice. There were some other ideas as well that may come in handy if my idea fails you for some reason. Hope it works for you! 

[http://ubuntuforums.org/showthread.php?t=2174237](http://ubuntuforums.org/showthread.php?t=2174237)

---

### Post by Quackers on 2013-09-15
Alternatively there are many sites which offer a download for Windows repair discs. You will need one with the same version of Windows as you have installed and the same architecture - ie 32 bit/ 64 bit.
You can then run the automated repair function from that disc. It may be necessary to run it 3 times before it is fixed.

As mentioned by Christian_Rabideau above, lilo may well be good enough.

---

### Post by CeejRab on 2013-09-15
*addendum* if you choose to use repair disks, be careful that you download from a trusted source. If its an iso or rar archive be wary and scan with antivirus just in case. 

(Above all, avoid torrents! Torrents are loaded with spyware, malware, etc. Although its quite unlikely that it could affect your linux computer, it can still have corrupt files on your HD and may infect someone else's computer if you plug in usb devices etc from your computer to theirs.)

---

### Post by oldfred on 2013-09-18
Moved to otherOS as Windows or Arch related.

Did you try to install Arch in UEFI mode? You have what looks like a typical BIOS/MBR Windows with a small boot partition and main install. But it says drive is gpt which is for UEFI booting. Windows only boots from gpt partitioned drives with UEFI. You also are showing two efi partitions, but in gpt the boot flag defines the efi partition where in MBR(msdos) the boot flag defined the Windows partition to boot from. You only can have one boot flag per hard drive.

You probably need to convert back to MBR and remove boot flag from sda2 as sda1 is boot partition. But you also have bootmgr & BCD in sda2, so may be able to directly boot that partition also.

I might try fixparts first, but you may need gdisk to fully convert. Fixparts is more for those cases where drive is both MBR and still has backup gpt partition table. If you have both primary and backup gpt tables you will need gdisk to do a full conversion.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

