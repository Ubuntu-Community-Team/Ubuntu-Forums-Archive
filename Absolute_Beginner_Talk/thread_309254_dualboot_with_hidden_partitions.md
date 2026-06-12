---
title: "dualboot with hidden partitions"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by daveblack on 2006-11-29
Hi 

I just recently started using ubuntu and I enjoy using it so far. 

Yesterday, I installed it. But the problem is, I'm sharing my computer with two others. So far I have used a boot manager to switch between the partitions (3 XP's), and, in each OS - the boot managet hides the other os' partition. 

Unfortunately, my boot manager doesn't seem to recognize ubuntu. so I need a boot manager which can both boot different OS and hide partitions depending on the os chosen - is there such a boot manager? can grub do this? 

thanks
dave

---

### Post by daniminas on 2006-11-29
Windows XP by default does not show the linux partitons..

---

### Post by nickburns on 2006-11-29
You will be able to see Widows from Ubuntu but no the other way around...

---

### Post by daveblack on 2006-11-29
thanks for the reply, daniminas.

> Windows XP by default does not show the linux partitons..

Yes, I noticed that. But the problem is that ubuntu installed grub and now when i open up my xp through grub I can see the other OS partitions. Also in ubuntu I can see all the partitions.

can grub hide partitions also? or maybe is there a way to run gparted befor grub to hide partitions? I'm clutching at straws here...

---

### Post by John E on 2006-11-29
Grub can't hide the partitions AFAIK. However, you can prevent them from being mounted at boot up. Login as **root** (or use **sudo** if you prefer). Navigate to the folder called **/etc** and you should find a document called **fstab**. Open it with a text editor and comment out any line that has an entry for a partition you don't want to mount. As usual, make a safety copy of it first.

---

### Post by daniminas on 2006-11-29
Windows shows you the FAT, NTFS partitions... Ubuntu shows all.. from ubuntu you can edit the /etc/fstab... and from Windows maybe with some program can hide FAT/NTFS partitions.. :-k

---

### Post by daveblack on 2006-11-29
Thanks for all the replies.

I found out after some googling, that my boot manager ([http://www.boot-us.com/](http://www.boot-us.com/)) does support linux - but only the LILO boot manager. Is there a way to install LILO instead of grub? or maybe I should ask: what is LILO? what's the difference between LILO and grub?

---

### Post by John E on 2006-11-29
I was reading about this the other day. Assuming the article was current, the main difference seemd to be that LILO has no awareness of file systems. It needs to know the precise sector(s) that each of your partitions starts on. Therefore, as long as nothing ever changes, you should be okay.

Grob, however, is "file system aware" and as such, it can call other boot managers such as Windows' "boot.ini". It's also slightly more forgiving if you re-size partitions (though not if you insert new ones or change the order).

Grub is probably the better one to use, if you can.

---

### Post by steve.horsley on 2006-11-29
It seems that GRUB can hide partitons - see this: [http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

I don't see why your current bootloader shouldn't be able to launch GRUB from the Ubuntu partition, but the Ubuntu installer seems to be broken and cannot install GRUB on the root partition instead of the MBR. It offers the option, but fails to install. It is possible to overcome this if you want, but it's messy. Let me know if you want the gory details.

---

### Post by daveblack on 2006-11-29
I'd love the detail if you don't mind. Please keep in mind though that I'm new to the whole linux experience. I'm not a computer newbie though, and terminals don't scare me. (I'm a programmer by hobbie).
Also, I coudn't find anything in the link you provided about hiding partitions, mayhap I missed it.
Also if you could provide detail that would work for kubuntu too because I'm now trying it too. (I fell in love with the kde look).

---

### Post by John E on 2006-11-30
> **daveblack said:**
> I'd love the detail if you don't mind. Please keep in mind though that I'm new to the whole linux experience.

Haha - I'm in the same boat - but if my experience is anything to go by, the fewer gory details you delve into, the better. :mrgreen: Steve's probably the best man for guiding you through the mire, though.  I always find his advice is very easy to follow!

> **daveblack said:**
> 
Also, I coudn't find anything in the link you provided about hiding partitions, mayhap I missed it.

It is there.... look in the section called **Installing GRUB**. Having said that, Linux might not subseqently recognise the partition(s) as being hidden. That's been my experience, anyway.

---

### Post by steve.horsley on 2006-11-30
> t is there.... look in the section called Installing GRUB. Having said that, Linux might not subseqently recognise the partition(s) as being hidden. 

No, I don't think Linux is fooled that easily. But the practical requirement is to hide one Windows installation from another.

Here's what I remember of the fun and laughter installing GRUB to the root partition of my Ubuntu install. The reason I did it was that I quad boot three different Linux installs and one XP. My bootsector has GRUB on it, and that GRUB uses files located on the first Linux install, which I keep as "rescue" Linux just in case I screw up the others. A rescue install is faster to boot than a live CD, and it provides a permanent home for the GRUB files.

The other two Linux's and XP are all booted with the same method from my master GRUB - root (hd0,x) and chainloader +1. Since the method of loading these partitions is the same for XP and Linux, I expect that a Windows bootloader should be able to cope too, though I have never tried one.

In my case, the partition that I wanted to install Ubuntu into was already there because it held a previous version - I just wanted to reformat and install into the same partition. But I don't think that's really important. I used the "alternate" installer because it seems more reliable than the live one. I'm not sure if the live one offers an option not to install to the MBR.

I chose custom partitioning, and specified all the mount points. When it came to installing the bootloader, I chose not to install on the MBR, and was asked to name a destination to install to. The installer always says I can use /dev/sda1 or (hd0,0) style partition names. I have always shosen to use the /dev style so far (and it always fails). Maybe I will try the GRUB notation next time. If that works, it will make things much easier.

As I say, installing the bootloder fails miserably, and I then choose to continue the installation without the bootloader installed. Once the installation is finished, Ubuntu cannot boot of course. Two things need doing - GRUB needs installing and a menu.lst file needs creating for it.

To install GRUB, boot the install CD again, and you can get the option to open a command prompt on a particular partition - it puts you there as root. It's a badly crippled command prompt (you can't use vi or nano for example), but it is enough to issue the command **grub-install /dev/sda6** (or whatever your partition is). 

Now GRUB is installed, but doesn't work because it can't find the /boot/grub/menu.lst file. I used a live CD and copied menu.lst from my old Dapper partition, and then manually edited the kernel and initrd names to match what was really there. Once this is done, you can boot the Ubuntu partition. For your pleasure and convenience, I attach my menu.lst from my Edgy install. You will still need to edit it to fix the partition names and maybe the kernel names.

Now all you need to do is to get the real bootloader to chainload the partition. As I said, I use GRUB, and this extract is from my MBR grub that chainloads the Edgy GRUB:
> title		Linux Edgy
root		(hd0,5)
chainloader	+1
boot


title		Linux Dapper
root		(hd0,6)
chainloader	+1
boot

title		Windows
root		(hd0,1)
makeactive
chainloader	+1


title		Linux rescue partition (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


So in summary:
1) Do the install, continue after it fails to install the bootloader to the root partition
2) Rescue disk, prompt on the new partition, grub-install /dev/?
3) Live CD, place a suitable /boot/grub/menu.lst in there.
4) Configure the real bootloader to chainload the partition.

Hope this works for you. 
If you discover that using the GRUB partition notation instead of /dev/? notation works, please let me know.

EDIT:
The web site didn't accept menu.lst. I'll rename it to menu.lst.txt and try to attach it again.

---

### Post by daveblack on 2006-11-30
Thanks alot steve. I'll try that and update here later how it went for the sake of others who might be interested.

---

