---
title: "Boot problems with fresh Dapper install with Win XP"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-06-02
Hey guys, sorry to be bothering with stupid questions like this..
I just installed 6.06 version of Ubuntu on a system which already runs Win XP. When I'm done installing and boot up, GRUB won't show up. It instantly boots up Win XP instead.

Is there anything I should try in order to solve this?
My mainboard is a MSI K8N Neo2-FX in case this might be BIOS related.

Thanks.

---

### Post by confused57 on 2006-06-02
[QUOTE=Nunyah]Hey guys, sorry to be bothering with stupid questions like this..
I just installed 6.06 version of Ubuntu on a system which already runs Win XP. When I'm done installing and boot up, GRUB won't show up. It instantly boots up Win XP instead.

Is there anything I should try in order to solve this?
My mainboard is a MSI K8N Neo2-FX in case this might be BIOS related.

Thanks.[/QUOTE]
No question is stupid in this forum, someone here will usually have a solution.
We were all utterly clueless in the beginning.

Do you only have one hd you're dualbooting with or a second hd(master/slave).?
When your system is booting up, is there a "Grub loading" press "Esc" to enter grub?  During the Dapper install, where did you opt to install grub?
Whatever other information you can give about your installation methods would help...did you run the LiveCD & install from it?, etc.

---

### Post by Nunyah on 2006-06-02
I have 2x 320 GB SATA disks which is used as NTFS storage disks and 1 250 GB SATA disk I use for system installs etc.

I'm running a 20 GB NTFS partition (for Win XP) and i made another 20 GB partition for Dapper Drake.
I do not have any GRUB at all, bootup acts like XP is my only system. Though the 20 GB partition for Dapper is in Ex3 format. (So I think it's installed correctly, just the boot handler which might cause problems)

**Install**
I installed Dapper running the live CD which gives me the option to do a complete install once X is running. I did **not** make a swap disk, as I'm running with 2 GB DDR RAM. (Should I still consider using a swap drive?)

When done installing, it prompts me to take out the CD and restart, but as mentioned, there's no GRUB comming up..

I guess it might be BIOS related problem as well..

---

### Post by confused57 on 2006-06-02
You definitely don't need a swap partition.
I'm not familiar with SATA drives ,especially if you're running a raid configuration.

You might want to boot up the LiveCD, open up the terminal, and type in:

```
cat /etc/fstab
```

and 

```
sudo fdisk -l
```

the -l is a lowercase "L"

You might want to post the results, I think this works with the LiveCD, & someone might be able to give you a solution.

---

### Post by Nunyah on 2006-06-02
I'm not running RAID. The way I run SATA, is just like I'd do with any other IDE disk, only I don't have to worry about master/slave.

I'll try to boot up and follow your instructions. I'll post the results here later when I'm done.

Oh and thanks, really appreciate your input.

---

### Post by lumpki on 2006-06-02
The thing you need to figure out, is where did you put Grub during installation? The default is to install it to the MBR. Otherwise you'll need to use a boot disk (or some other boot manager in the MBR to point to the partition where GRUB lives) to start up Ubuntu.

It doesn't hurt to have a small swap partition (512MB or so) no matter how much RAM you have. If you want to add swap after installing, you can use a swap file instead of a separate partition. Use the mkswap and swapon commands, see the manual pages for details (or start a new thread.)

---

### Post by Nunyah on 2006-06-02
I diddn't choose to do anything special with the GRUB (diddn't even have that option). The last thing the installer did before I got prompted to reboot, was to install and set up grub..

Here's screenshots. It's from the live cd, though. Not sure if that matters..

---

### Post by confused57 on 2006-06-02
Have you seen this tutorial:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

I did a search for Ubuntu installation on SATA drives and a lot of people have had problems installing grub to a SATA drive.  I saw someone disconnected all drives, except the one they were installing Ubuntu onto...then reconnected the other drives after installing.  Some mentioned doing an expert install?

I've never used the espresso GUI LiveCD installer, but the text-installer on the alternate CD detects another OS when installing grub and recommends installing onto the mbr.

Sorry I can't help you, but you may want to read some of the problems people have had installing on a SATA drive...Best of luck.

---

### Post by JediLow on 2006-06-02
Try booting off the other hard drive... it was a problem that I was having (my BIOS was booting off the wrong HD, I was having errors and couldn't run anything as a result)

---

### Post by Nunyah on 2006-06-02
The guide only explains how to perform the install. (Not technical problems and such)

I guess SATA could be the source of trouble here, I've never had trouble with the boot manager before when I've used IDE drives..
The alternate CD, is that Kubuntu? I can try and see if it makes a difference..

Also, I'm gonna disconnect my other two sata drives, just in case..

---

### Post by keith whitehouse on 2006-06-02
Hi Nunyah,

I have a pair of SATA drives, the larger one (disc 1) is where Windows still sits, and the second one is where I am installing Ubunto. I have spent the last 6 hours trying to get it done, but I do NOT have any trouble with the SATA drives, just the partitions on the second drive.

best regards keith

---

### Post by confused57 on 2006-06-02
[QUOTE=Nunyah]The guide only explains how to perform the install. (Not technical problems and such)

I guess SATA could be the source of trouble here, I've never had trouble with the boot manager before when I've used IDE drives..
The alternate CD, is that Kubuntu? I can try and see if it makes a difference..

Also, I'm gonna disconnect my other two sata drives, just in case..[/QUOTE]

You could try Kubuntu, but I was referring to the Dapper-alternate CD, which is the install CD and has a text installer.  I find the text installer is easier for me and it asks where to install grub, I always select mbr.  Let us know how it goes.
Here's an interesting article on Linux and SATA:
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

I'm not being much help, but at least I keep bumping your thread...

---

