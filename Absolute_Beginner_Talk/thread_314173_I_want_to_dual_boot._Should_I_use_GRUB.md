---
title: "I want to dual boot. Should I use GRUB?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-07
I'm an XP user. I just downloaded and burnt Ubuntu 6.10. I do not know what boot loader to use. Should it be NTLDR, LILO or GRUB?

---

### Post by Odisej on 2006-12-07
Grub is the standard. I had no problems using it so I would recommend it to you as well.

I am not an expert to explain the differences between the three but Grub does the job and in my experience there are more people using it than the other two. I also believe the Ubuntu team chose it to be the default for a reason. Whenever I searched for help and support for Grub it was quick and painless. 

Regards,

Odisej

---

### Post by wersdaluv on 2006-12-07
Should I download GRUB Legacy or GRUB 2?

---

### Post by slimdog360 on 2006-12-07
The ubuntu disk provides and does everything for you. You dont need to install or configure anything but Ubuntu.
Remember to back up your XP drive just incase.

---

### Post by Sef on 2006-12-07
> Should I download GRUB Legacy or GRUB 2?

GRUB will automatically install.

Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for how to install the alternate cd.

Read [Psychocats Installing]("http://www.psychocats.net/ubuntu/installing"), for how to install the live cd.

---

### Post by wersdaluv on 2006-12-07
After installing Ubuntu, will it be automatically ready for dual booting?

---

### Post by Duck2006 on 2006-12-07
Yes it will be able to Dual Boot after install

---

### Post by Subw00fer on 2006-12-13
> **Duck2006 said:**
> Yes it will be able to Dual Boot after install

Hi everyone!  This is my first post and I am new to using Ubuntu on my home pc since I just installed it late last night.  I've been using Linux for about 6-7 years now but I am new to having a dual boot system.

I have two hard drives in my PC (master SATA with WinXP and slave IDE with Ubuntu 6.10) and I had the installer set GRUB to hd0.  When I rebooted my system, it did not give me an option to either boot into WinXP or Ubuntu and it went straight into Windows OS.  How do I get into Ubuntu and should I be using GRUB....if I am using it at all?

thanks

---

### Post by bulldog on 2006-12-13
Try to boot from the other disk.
There's a fair chance it's installed in there.
The Sata--IDE mix-up.
If it's there you have to set the menu.lst to the right partitions.
Not hard to do,just let me know.

---

### Post by Subw00fer on 2006-12-13
> **bulldog said:**
> Try to boot from the other disk.
There's a fair chance it's installed in there.
The Sata--IDE mix-up.
If it's there you have to set the menu.lst to the right partitions.
Not hard to do,just let me know.

I was only able to boot up the Live CD and I was unable to find the menu.lst file or the GRUB installation if it was done there.  When I installed it, it went to hd0 which I am unfamiliar with since the second hard drive was hdb1 and the primary one was sda.

I also need to get my wireless internet working in Ubuntu so that I don't have to reboot and get back into windows just to type this message.

Any suggestions for how to get the NTLDR or GRUB menu to show when I boot up my PC?

---

### Post by Subw00fer on 2006-12-13
I see that menu.lst should be located at /boot/grub and I did not see it when I loaded the LIVE CD.  Does this sound correct or should I try reinstalling Ubuntu on my IDE slave hard drive and change the location of GRUB to something else besides hd0?

Also, I noticed that on the Windows XP side there was only a boot.ini.backup file located at C:/Windows/pss and it looked like:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


Any help?  thanks guys

---

### Post by Subw00fer on 2006-12-13
Anyone know what I should do?  I'm almost thinking about reinstalling Ubuntu on my second harddrive and just pointing GRUB to that drive.

---

### Post by Subw00fer on 2006-12-14
I hope someone can answer these questions that I have but perhaps the reason that I am not able to boot up the second hard drive is that it is not being read.  Since it is IDE, I took one of the cables that was coming from my two CD drives and pluged it into my 2nd hard drive.  I figured this would work because when I booted up windows, it recognized the drive and I was able to access it.  But once I installed Ubuntu on that drive, I am unable to see it in Windows XP which is expected but I can't figure out why it wont let me boot into it.

Would this be causing my NTLDR or GRUB problem?

---

### Post by confused57 on 2006-12-14
> **Subw00fer said:**
> I hope someone can answer these questions that I have but perhaps the reason that I am not able to boot up the second hard drive is that it is not being read.  Since it is IDE, I took one of the cables that was coming from my two CD drives and pluged it into my 2nd hard drive.  I figured this would work because when I booted up windows, it recognized the drive and I was able to access it.  But once I installed Ubuntu on that drive, I am unable to see it in Windows XP which is expected but I can't figure out why it wont let me boot into it.

Would this be causing my NTLDR or GRUB problem?
As Bulldog mentioned, you should be able to set your bios to boot first(does your bios recognize the IDE drive?) to the Ubuntu IDE drive...if Ubuntu will boot, it's simple to add an entry to boot Windows from grub.  Since your system boots to Windows, then it's probable that grub was installed to your IDE drive(hd0).

The key is that grub recognizes your IDE drive as hd0, regardless of whether it's actually hdb, hda, etc.

---

### Post by gn2 on 2006-12-14
Don't know if this may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by macogw on 2006-12-14
subw00fer, it's because Windows is the primary drive.  Set ntldr to chainload grub or make the Ubuntu drive be primary and Windows is slave.  hd0 is just what Grub calls the drives.  It's nothing to do with what /dev is calling them, because it hasn't even really looked there yet.  Usually, hd0 means the drive that Grub is installed on and hd1 means "that other drive over there".

---

### Post by louieb on 2006-12-14
Did you try what Bulldog asked and make your other hard drive the  first boot device? You will probably have to use BIOS setup. 
What were the results?
Try that first. 
Second Boot to Live CD
Open Applications > Accessories > Terminal
and run
```
sudo fdisk -l
```However you can it would be a great help if you could post the output here.

---

### Post by Subw00fer on 2006-12-14
> **confused57 said:**
> As Bulldog mentioned, you should be able to set your bios to boot first(does your bios recognize the IDE drive?) to the Ubuntu IDE drive...if Ubuntu will boot, it's simple to add an entry to boot Windows from grub.  Since your system boots to Windows, then it's probable that grub was installed to your IDE drive(hd0).

The key is that grub recognizes your IDE drive as hd0, regardless of whether it's actually hdb, hda, etc.

This seems to be what is going wrong with my install.  When I opened up the BIOS, I did not see the IDE drive listed as the primary or seconardy master or slave.  How do I get the BIOS to see that new drive?  Right now there are three drives that it recognizes (my DVD drives) and the blank spots are set to "Not Detected" if I remember correctly.  I guess I should set them to "Auto".  Is that correct or is there another way to get the BIOS to see the second IDE HDD?

If I try to reinstall Ubuntu and set GRUB to install on "sda" which is the master drive with WinXP on it, will that format my drive and/or will I have issues with getting onto that OS as well?

I'll try some things out tonight and post them here.  The best situation for me would to not have to change the IDE drive to master and the SATA drive to slave.  

I would try to install LILO but how can I do that if I can't even get into the second hard drive now.  I think my main objective is to get the BIOS to recognize the second drive (even though the install saw it but perhaps thats because it is now formatted for linux) and then to get booted into Ubuntu so that I can configure my wireless.

---

### Post by bulldog on 2006-12-14
The file system [ext3 or NTFS] is not important to the BIOS to recognize your disk.
Did you connect the IDE cable correct on the master IDE port,and did you have a look at the jumpers at the back of your disk?

If they are set as slave and you connect it with the master IDE port,or vice versa,your disk is probably not recognized.'
Installing Lilo will not help in this matter.

Just check your hardware!!!

---

### Post by Subw00fer on 2006-12-14
> **bulldog said:**
> The file system [ext3 or NTFS] is not important to the BIOS to recognize your disk.
Did you connect the IDE cable correct on the master IDE port,and did you have a look at the jumpers at the back of your disk?

If they are set as slave and you connect it with the master IDE port,or vice versa,your disk is probably not recognized.'
Installing Lilo will not help in this matter.

Just check your hardware!!!

I have three IDE ports on my motherboard (two for the CD drives and one for the floppy).  So I noticed that both CD drives had an extra IDE cable splitter and I connect the second hard drive to one of those.  I figured this was alright since when I first booted up in WinXP, it recognized it.  Should I try a different config for my IDE cables?

---

### Post by cacharreo on 2006-12-14
Grub, of course:-D

---

### Post by bulldog on 2006-12-14
You can't use the Floppy 'IDE' :D 

You have two IDE ports,and on each port you can use two devices.
This would be the primary master and primary slave and the secundary master and secundary slave.
This could be a hard disk and a CD-rom player or two hard disk,or two cd-rom-players.

The only thing you have to take care of  if you use more than one device on a IDE port is,you have to set one device as a master and the other as a slave device.
This is done by setting jumpers on the back site of the device in the right order.

Mostly if you connect a hard disk and a cd-rom device to the same IDE,you set the hard disk as master and the cd as slave.
It should be a wise thing to use the primary master IDE first.

This all must be accomplished before your BIOS can detect the hardware properly.
So turn off the computer and disconnect the power cable from the outlet.
And start to reconfigure your hardware,you should have some documentation which came along with the computer.

If this is done properly,you can ask me what to do next.
If you ran into trouble,don't panic but give a shout.:D

---

### Post by Duck2006 on 2006-12-14
> Mostly if you connect a hard disk and a cd-rom device to the same IDE,you set the hard disk as master and the cd as slave. It should be a wise thing to use the primary master IDE first.

If the system is a HP or a Compaq the CDROM must be the secondary master, for some reason. HP's see the CDROM a drive M in some of there systems

---

### Post by Subw00fer on 2006-12-14
Bulldog, thank you very much for your help.  I took the cable from my CD drive and plugged that into the IDE drive and then enabled it within the BIOS.  Now everything, inclduing GRUB, is working perfectly.

The only thing that I need to get working now is my wireless internet so that I can post on this site from my Linux hard drive.  Any good links on how to set a Linksys wireless router?  The other thing that I need (but its not critical) is to be able to read files from the first drive onto the second one.

---

### Post by Subw00fer on 2006-12-15
I know this isn't a GRUB related question, but I had such great help in here and especially from Bulldog.....I was wondering if I could get some help with how to get my wireless internet working.  I'm not even sure where to start!  I've been searching these forums but I can't figure out which one to read and even the ones I read are not helpful

---

### Post by jbayone on 2006-12-15
Super Grub is also nice to have as a rescue utility.

---

### Post by bulldog on 2006-12-15
> **Subw00fer said:**
> I know this isn't a GRUB related question, but I had such great help in here and especially from Bulldog.....I was wondering if I could get some help with how to get my wireless internet working.  I'm not even sure where to start!  I've been searching these forums but I can't figure out which one to read and even the ones I read are not helpful

Well I'm not a wireless users so I can't be of much help.
If you go to System-> Administration->Network is there a wireless connection setup?
I read things about ndiswrapper so you could use drivers from windows,but I'm not really in to this.
I prefer a nice ethernet cable with my router,which is capable of wireless though.

---

### Post by Kazna on 2006-12-15
> **Duck2006 said:**
> st.

If the system is a HP or a Compaq the CDROM must be the secondary master, for some reason. HP's see the CDROM a drive M in some of there systemsThats with many systems  not limited to HP alone. Most CD drives will have to be Master to function correctly.

---

### Post by bulldog on 2006-12-15
What I know of hardware is you can simply jumper it as a slave device.
This should work very well,must admit I build my PC by myself,and never had a Dell or HP or what ever,but can't imagine it has anything to do with the manufacturer of the hardware.

Mostly there'r just one hard drive on the first IDE and a cd-rom at the second IDE which is perfectly normal in that case,so they both are set as master.
But if you want more hardware like a new hard disk or a burner,you have to have the possibility to switch the drives from master to slave.

---

### Post by Subw00fer on 2006-12-17
I figured I would post this question here and hopefully someone has an answer:

I have Ubuntu on an IDE (fat32) hard drive and WinXP on a SATA (ntfs) hard drive.  Is there a way so that I can access both drives in either OS?

---

### Post by mdsmedia on 2006-12-17
> **Subw00fer said:**
> I figured I would post this question here and hopefully someone has an answer:

I have Ubuntu on an IDE (fat32) hard drive and WinXP on a SATA (ntfs) hard drive.  Is there a way so that I can access both drives in either OS?

Have a look at:

[http://www.psychocats.net/](http://www.psychocats.net/)

This is a great resource for your basic Ubuntu needs, from a user who knows what it's like to be new to Ubuntu.

There are many threads on this particular topic if you do a search on the Forums, but I'd suggest if you don't find what you need, start a new thread on the new topic simply because people who know how to help with that particular problem are more likely to see it, rather than a problem with GRUB.

---

