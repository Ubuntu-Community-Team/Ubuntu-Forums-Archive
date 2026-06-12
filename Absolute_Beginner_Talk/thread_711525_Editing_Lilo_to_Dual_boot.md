---
title: "Editing Lilo to Dual boot"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by mjj808 on 2008-02-29
Hey there folks. I've installed Ubuntu and I am very happy so far, the only problem is that I cannot boot Windows (I know, real original problem). During the install, I could not install GRUB, so I am using LILO instead. 

I am sort of a hasty installer and do more leaping than looking. I made a new partition on my main harddrive and installed Ubuntu there. I believe it is the second partition now (sda2?). I think Windows is sitting on sda1, but I'm not sure. 

I have searched all over here, and tried various solutions, but I am still just getting Ubuntu. Can some please help me figure out:

-How to edit the lilo.conf file so that it gives me a choice of OSs? I have already tried a couple of modifications.

my fdisk -l is:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27851   210551688+   7  HPFS/NTFS
/dev/sda2           27851       31237    25598976    7  HPFS/NTFS
/dev/sda3           31238       32301     8043840    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14593   117218241    7  HPFS/NTFS

``` 

The sda 2 is weird, because the system monitor actually says it is an ext3 file system, which is what it should be for Linux, right?

I'm very new at this, as you can see. Please tell me what other info is needed, and what I should try. 

Thank you!

Matt

---

### Post by LinuxGuy1234 on 2008-02-29
> **mjj808 said:**
> Hey there folks. I've installed Ubuntu and I am very happy so far, the only problem is that I cannot boot Windows (I know, real original problem). During the install, I could not install GRUB, so I am using LILO instead. 

I am sort of a hasty installer and do more leaping than looking. I made a new partition on my main harddrive and installed Ubuntu there. I believe it is the second partition now (sda2?). I think Windows is sitting on sda1, but I'm not sure. 

I have searched all over here, and tried various solutions, but I am still just getting Ubuntu. Can some please help me figure out:

-How to edit the lilo.conf file so that it gives me a choice of OSs? I have already tried a couple of modifications.

my fdisk -l is:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27851   210551688+   7  HPFS/NTFS
/dev/sda2           27851       31237    25598976    7  HPFS/NTFS
/dev/sda3           31238       32301     8043840    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14593   117218241    7  HPFS/NTFS

``` 

The sda 2 is weird, because the system monitor actually says it is an ext3 file system, which is what it should be for Linux, right?

I'm very new at this, as you can see. Please tell me what other info is needed, and what I should try. 

Thank you!

Matt

Do:
```
gksudo gedit /etc/lilo.conf && sudo /sbin/lilo
```
In gedit, add entires like:
```
image = /boot/vmlinuz
  root = /dev/hda1
  label = Linux
  read-only
  initrd = /boot/initrd.gz
```
Or like:
```
other = /dev/hda3
  label = WindowsXP

```
Save it and quit gedit. LILO should now pick up the new options and add it to it's menu.

---

### Post by glennric on 2008-02-29
Something is definitely wrong.  I am not sure, but I do not believe linux can run from an NTFS partition.  So you currently can boot to linux as it is?  I would say delete that partition and reinstall linux.  Then it should be able to install grub.

---

### Post by mjj808 on 2008-02-29
> **LinuxGuy1234 said:**
> Do:
```
gksudo gedit /etc/lilo.conf && sudo /sbin/lilo
```
In gedit, add entires like:
```
image = /boot/vmlinuz
  root = /dev/hda1
  label = Linux
  read-only
  initrd = /boot/initrd.gz
```
Or like:
```
other = /dev/hda3
  label = WindowsXP

```
Save it and quit gedit. LILO should now pick up the new options and add it to it's menu.

Thanks for the reply. What does it mean to gedit both the lilo.conf file (which was all I was doing before) and also the /sbin/lilo part? What does that second part after the && do?

Ooh, ok, that command did something, because I got this back:
```
sudo gedit /etc/lilo.conf && sudo /sbin/lilo
Added Linux *
Added LinuxOLD
Warning: CHANGE AUTOMATIC assumed after "other=/dev/sda1"
Added Windowsvista808
Fatal: RESTRICTED is only valid if PASSWORD is set.

```
But what's up with that fatal error? Should I set a password in the conf file or something?

I'm going to restart now and see if anything happens different, and then check back here. 

Thanks very much.

Matt

---

### Post by mjj808 on 2008-02-29
No, just went right to "starting Linux" as usual. I may have made a mess of the conf file before.

---

### Post by LinuxGuy1234 on 2008-02-29
> **mjj808 said:**
> Thanks for the reply. What does it mean to gedit both the lilo.conf file (which was all I was doing before) and also the /sbin/lilo part? What does that second part after the && do?

Ooh, ok, that command did something, because I got this back:
```
sudo gedit /etc/lilo.conf && sudo /sbin/lilo
Added Linux *
Added LinuxOLD
Warning: CHANGE AUTOMATIC assumed after "other=/dev/sda1"
Added Windowsvista808
Fatal: RESTRICTED is only valid if PASSWORD is set.

```
But what's up with that fatal error? Should I set a password in the conf file or something?

I'm going to restart now and see if anything happens different, and then check back here. 

Thanks very much.

Matt

"gksudo gedit /etc/lilo.conf" means "open gedit to /etc/lilo.conf to root". The "&&" means "if the command completed, do the action after this". The "sudo /sbin/lilo" part means "update LILO's menu."
-----------Off the lesson--------
Then add a password line (replace test with a easy to remember password):
```
password = test
```
Now run:
```
sudo /sbin/lilo
```
-Or-
Remove restricted from everywhere in your /etc/lilo.conf and again:
```
sudo /sbin/lilo
```

---

### Post by mjj808 on 2008-02-29
Whoo hoo! I tried various wranglings, but it kept booting right into Linux. Then, I tried hitting "ctrl" when Lilo showed up, and voila! The lilo menu came up, with the OS boot options I had added. Actually, there were a ton of them, because I kept adding them over and over in the conf file. Sweet. I am posting this from my windows os now. 

Thank you very much. I had a feeling it was going to be nice like this over on this side of the software divide. A truly helpful user/developer community=PRICELESS

Thanks,

Matt

---

