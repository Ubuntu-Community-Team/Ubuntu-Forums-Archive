---
title: "Going to install Ubu, multiboot, HOW ?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Ayush on 2006-11-23
I have :
C:\   Windows
D:\   Data1
Blank Space [5.7 gb] Want to install Ubu on it
Blank Space [1 gb] For Swap use
E:\   Data2


If i install Ubuntu (5.10), how can i multi boot with XP ? Please tell me as clear as possible and all the steps. I dont think i will be able to connect to internet using Ubuntu so if any method told here fails, i cant boot in windows and cant connect to internet (dial-up) so i will be stuck with some basic applications !!](*,)!! I don't have XP Setup disk so i cant repair/reinstall windows. I want to be able to multi-boot with WinXP Pro and Ubuntu .

---

### Post by Bachstelze on 2006-11-23
You'll have nothing to do. The Ubuntu installer will detect your Windows and automagically configure GRUB to dual-boot :)

---

### Post by Ayush on 2006-11-23
OK, but what to do if it doesn't ?? I stated that i will not be able to do anything if this kind of thing happen. At which step, will it tell me that it recognized my Windows ?

---

### Post by Bachstelze on 2006-11-23
During the install, when it will install HRUB, it should tell you something like "The following operating systems were detected on your drive, do you want ton install GRUB on the MBR ?" Windows will appear so you'll be safe installing GRUB on the MBR.

---

### Post by Rui Pais on 2006-11-23
> **Ayush said:**
> OK, but what to do if it doesn't ?? I stated that i will not be able to do anything if this kind of thing happen. At which step, will it tell me that it recognized my Windows ?

Being cautious is an excellent approach to a product that you didn't know well. 

Try to make a liveCD with Ubuntu, the same that you will use to install Ubuntu if you wish. You can run Linux from the liveCD without touch your harddisk.

If it runs without problems that may assures you that it will install successfully or at least that any minor problem can be solved. Try to get used to it too, in the mean time.

When you install one of the most important steps is the partition detection. Thats when it will find your Windows installation. It's done graphically with an application called gparted. 

You can run gparted from the livecd and check if your windows/partitions are beeing correctly detected.

Most of the problems are not if Linux recognize Windows but the other way around... If you need to reinstall Window you will need to reinstall the Grub (boot manager) again cause windows will install "over" it (delete it from MBR )

---

### Post by Carlos Santiago on 2006-11-23
Ayush, first of all why dont you try at least version Ubuntu 6.06? It is very stable, and detected all my hardware!

I as Rui Pais said, you can run a LiveCD. 

The LiveCD of Ubuntu 6.06 is also the install CD, but it wont touch your hard drive unless you click on 'Install'. We all assure you that. ;-)

With the liveCD you have all the system features that you would have if the system was install on hard drive. The difference is that when you restart your PC you will be back on your old MS System.

You said that you wont be able to connect to internet. Why?
What kind of internet connection do you have?

---

### Post by namah on 2006-11-23
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html)

---

### Post by Ayush on 2006-11-23
I am on Dial-up. I said that before. I think my CD is not good now because i am getting same error at same point when installing and with two different drives. I tried 4 times. I requested the free CD. I will wait for that.
My question now is :
As you all said that setup will automatically dual-boot and it did. Now because i couldnt install it correctly, i want to clear the dual-boot from MBR. How can i do it ?

---

### Post by steve.horsley on 2006-11-23
You are right to be cautious.

If you have a live CD and a USB stick, you can take the precaution of making a backup copy of your partition table and bootloader.

From the live CD GUI, open a command prompt (Applications->Accessories->Terminal) and enter the following command (if you have an IDE disk):
**sudo dd if=/dev/hda of=BOOTSECTOR bs=512 count=1**
or this command (if you have a SATA disk):
**sudo dd if=/dev/hda of=BOOTSECTOR bs=512 count=1**
Now insert the USB stick and use the file manager to copy the file to the stick. Make sure to right-click and eject the icon for the memory stick rather than just pulling it out.

If the installation goes wrong, you can restore the bootloader and partition table like this:
Start the live CD. 
pen the file exprorer (opens on your home folder). 
Insert the USB disk and another file explorer opens. 
Drag the BOOTSECTOR file from the USB disk to your home folder.
Start a command prompt (Applications->Accessories->Terminal)
Enter the following command (if you have an IDE disk):
**sudo dd if=BOOTSECTOR of=/dev/hda**
or this command (if you have a SATA disk):
**sudo dd if=BOOTSECTOR of=/dev/hda**

This will restore your bootloader and your partition table. If you chose to shrink the Windows partition (to make room for Ubuntu) after taking the image, then Windows will think it has a smaller partition than it really has. There may be some Windows tools that can fix that. The safe approach would be to shrink the Windows partition with Partition Magic and **then** take the bootsector image.

P.S.
I have used this precaution in the past, and been **very glad** that I did. Under some rare circumstances, the Ubuntu installer/partitioner can corrupt the partition table, rendering the Windows partition unreadable because it's not where the table says it is.

---

### Post by ImmigrantUS on 2006-11-30
What you really asking about is - Dual Boot. Since you only talking about two OSs. So if you search forums for it, there are lots of info, e.g. -> [http://ubuntuforums.org/showthread.php?t=282018]("http://ubuntuforums.org/showthread.php?t=282018") :). 

  Also partitioning basics -> [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning"),

   and installation pictorial tutorial -> [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

   Good luck!

---

### Post by Ayush on 2006-12-01
[ImmigrantUS]("http://ubuntuforums.org/member.php?u=202082"), []("http://ubuntuforums.org/showthread.php?t=282018")I learned a lot about how Linux name partitions from the link [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
As my last post says, i dont have Linux now. I am waiting for the free CD. The status shows :
1           CDs approved and sent to the shipping company in           2006-11-27
Great news, isn't it ?

---

