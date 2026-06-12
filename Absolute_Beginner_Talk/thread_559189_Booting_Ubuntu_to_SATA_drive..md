---
title: "Booting Ubuntu to SATA drive."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by 469tc on 2007-09-24
I am hoping someone can help me with booting Ubuntu to a SATA hard drive. I previously had a dual boot IDE hard drive with Windows XP and Ubuntu. I never experienced any problems until the IDE hard drive gave up the ghost. I then purchaced a SATA drive and partitioned it for dual boot  to Windows XP and Ubuntu, the same as I did on my IDE drive. I first installed XP and then Ubuntu, again the same process as my IDE drive. The Ubuntu install goes through without errors but when attempting to boot I just get fired into the XP partition. The GRUB boot menu does not appear. I then attempted to install Super GRUB. The boot menu would then appear, giving me the option to boot to XP or Linux kernel, but gave me an error 21(disc not found) when attempting to boot. I then could not boot into XP or Ubuntu. I had to reinstall the XP MBR. After spending much time with no resolution I purchased another SATA hard drive and installed this into another SATA port. I again installed Ubuntu with no errors, this time on its own, no XP,  but still the system will not boot. Can somebody please, please help! I miss my Ubuntu!

Thanks!

Todd:)

---

### Post by Pumalite on 2007-09-24
Post:(with Live CD):
sudo fdisk -lu

---

### Post by 469tc on 2007-09-24
I'm terribly sorry, I am so new to this that I don't know what you mean. Can you please clarify? Thanks and I definitely appreciate any patience you might have with a very new and clueless user like me!:confused:

Todd

---

### Post by Pumalite on 2007-09-24
I assume you have an Ubuntu OS in your internal drive. If so, go to Applications>Accessories>Terminal: the type: sudo fdisk -lu

---

### Post by danny joe ritchie on 2007-09-24
I think he means for you to boot up using the live CD, then go to the terminal and type = sudo fdisk -lu.
Post the output ! Sorry for repeating,but I'm not very fast at typing

---

### Post by 469tc on 2007-09-24
I assume that means I should boot to the Ubuntu desktop with the live CD, right?

---

### Post by 469tc on 2007-09-24
I think I just got my answer. I wiil attempt and post the results in a bit. Is there anything else I should look for or do after entering this command in the terminal window?  Not sure what it does??

---

### Post by Pumalite on 2007-09-24
If you don't have an Ubuntu OS in internal drive; yes, that's the other option.

---

### Post by 469tc on 2007-09-24
Sorry Danny, forgot to say thanks!:)

---

### Post by Shazaam on 2007-09-24
What it does is list your hard drives and partitions. It is needed to help fix your problem.

---

### Post by Pumalite on 2007-09-24
Post the output (copy and paste)

---

### Post by danny joe ritchie on 2007-09-24
Not a problem!

---

### Post by 469tc on 2007-09-24
Pumalite, I do have the OS on an internal drive but I just can't get to it. Is this what you meant? The live CD boots just fine.

---

### Post by Pumalite on 2007-09-24
In the Live CD go to the Terminal ,input the command and post the output.

---

### Post by 469tc on 2007-09-24
Thanks for all the help guys, I will boot with the live CD in a bit and post the results. I have to take a quick break for some dinner. Thanks again for the support!

Todd

---

### Post by 469tc on 2007-09-24
Many thanks to Shazaam as well!

---

### Post by 469tc on 2007-09-25
Ok guys,

Here is the info I received from using the fdisk -lu command at the terminal using the live CD:




ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   144584999    72292468+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   409593239   204796588+   7  HPFS/NTFS
/dev/sdc2   *   409593240   620526689   105466725   83  Linux
/dev/sdc3       620526690   625137344     2305327+  82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   512007614   256003776    7  HPFS/NTFS
/dev/sdd2       512007615   609666749    48829567+  83  Linux
/dev/sdd3       609666750   619434269     4883760   82  Linux swap / Solaris



The  two 37G drives shown are my Windows raid setup. The third drive is the first SATA drive I attempted to install Ubuntu to(also partitioned for Windows). The fourth drive is the drive I attempted to install Ubuntu to by itself. I have since partitioned this drive for a Windows install as well since it didn't seem to matter either way.

Hope one of you awesome gurus can provide me with an answer!

Thanks again!

Todd

---

### Post by 469tc on 2007-09-25
Pumalite,

By the way, I love the proverb about time and the teacher...

---

### Post by 469tc on 2007-09-25
Have any of you guys had a chance to analyze the info I provided?? I'm waiting patiently (well somewhat anyway)...:)

---

### Post by Pumalite on 2007-09-25
Your Raid Array is one problem. This is another: Disk /dev/sda doesn't contain a valid partition table
Grub usually installs to sda so, I'm not surprised of your failure.
Get this to test your drives:[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Get rid of your Raid Array if you can. (You will loose data)

---

### Post by 469tc on 2007-09-25
> **Pumalite said:**
> Your Raid Array is one problem. This is another: Disk /dev/sda doesn't contain a valid partition table
Grub usually installs to sda so, I'm not surprised of your failure.
Get this to test your drives:[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Get rid of your Raid Array if you can. (You will loose data)

But I don't understand. The RAID array has always been there and has not changed in any way since I went to SATA instead of IDE for the single drives. I installed Ubuntu to IDE with the RAID system intact and operational with no problems.  I have never attempted to boot to RAID in any manner when installing Ubuntu. Why would GRUB install to sda when I have set the BIOS to boot from CD to another drive? The GRUB menu never appears and never has when I set the BIOS to boot to RAID, it simply boots to Windows. I suppose I could disconnect all drives except the drive for Ubuntu before install so there is no question as to where GRUB might be installed. Maybe you bring up a good point...Think I wil try this. Thanks for the response.

Todd

---

### Post by Pumalite on 2007-09-25
I suppose I could disconnect all drives except the drive for Ubuntu before install so there is no question as to where GRUB might be installed.

That is a good idea.

---

### Post by 469tc on 2007-09-28
Pumalite,

Thank you so much! You helped me greatly, albeit in a sort of indirect way. You put an idea in my head. Instead of disconnecting the RAID drives or removing them completely (which I was not willing to do since this is my gaming drive) I simply disabled the SATA 1 and SATA 2 channels in the BIOS (the RAID drives). Now there was no way GRUB or Ubuntu could recognize these drives as they do not exist. I ran sudo fdisk -lu to verify on the live CD.  Install of Ubuntu and GRUB went without a hitch on both 320G hard drives!  I then enabled SATA 1 and SATA 2 via BIOS. I now have 5 working operating systems(3 Windows and 2 Ubuntu).  Thanks again for your input 'cause I was ready to give up. I am so happy to once again be able to use this awesome OS!!!:):):popcorn:

---

### Post by Pumalite on 2007-09-29
You are most welcome. Happy Ubuntuing!

---

