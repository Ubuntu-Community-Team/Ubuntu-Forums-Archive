---
title: "Windows XP will not boot the Live cd"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-03-25
okay, i burned a copy of 6.10 and it will start up on my laptop just fine (fedora core 5) but my main computer (windown xp) won't boot it up. it's bugging me. help anyone?

---

### Post by kittyhawk63 on 2007-03-25
> **silentjudas said:**
> okay, i burned a copy of 6.10 and it will start up on my laptop just fine (fedora core 5) but my main computer (windown xp) won't boot it up. it's bugging me. help anyone?

Place it in the CD Rom drive, Restart by pressing ctrl-alt-delete.
I've had no problem getting it to run under WinXp.
What speed did you burn the ISO?
Do you have your BIOS set so that it can boot from your CD Rom drive?

---

### Post by silentjudas on 2007-03-25
i have started the comp with the cd in the drive before, but i have never used plain reset. does it matter?

also: burned at maximum

---

### Post by taurus on 2007-03-25
Check the BIOS of your machine to make sure you have CD-ROM first in the boot order.  Otherwise, it will boot from your harddrive first.

---

### Post by silentjudas on 2007-03-25
oooh, i have to put that as first? ...oh, ok, makes sense now. i use it under second, alright, i'll try that. ty!

---

### Post by Frak on 2007-03-25
Burn at slow speeds, it helps to protect from disc errors from writing.
and are these partitions on the same hard drives?

---

### Post by kittyhawk63 on 2007-03-25
> **silentjudas said:**
> i have started the comp with the cd in the drive before, but i have never used plain reset. does it matter?

also: burned at maximum

A cold boot or a soft boot will give the same results.
You should never burn higher than 4x. Too many problems with bad data copying. Everyone here advises no higher than 4x.

---

### Post by silentjudas on 2007-03-25
nah, i checked it using my top, i think it jsut might be due to not having my cd set first in my BIOS, like taurus said

---

### Post by rodrigo juarez on 2007-03-25
Most computers come preconfigured to search for boot media from CD-ROM only after seeking to boot from HDD, you should check your BIOS settings to put CD-ROM on top of HDD from the boot options. It would be hitting del, F1, F2 or something like that while startin-up the computer, depending on your computer's manufacturer.

---

### Post by Drakkor on 2007-03-25
Yep, XP doesn't boot anythnig, it's an OS that is booted to. Your grub or mbr will tell it what to boot !

---

### Post by kittyhawk63 on 2007-03-25
> **silentjudas said:**
> nah, i checked it using my top, i think it jsut might be due to not having my cd set first in my BIOS, like taurus said
Follow Taurus's recommendation. Every time.

---

### Post by silentjudas on 2007-03-25
heh good news, i'm typing this from the lovely live cd. pwn.

taurus  was correct, i had to fix the bios up. Thanks for everyones help. i hope this post helps newbies in the future!

---

### Post by ububaba on 2007-03-31
> **taurus said:**
> Check the BIOS of your machine to make sure you have CD-ROM first in the boot order.  Otherwise, it will boot from your harddrive first.
My CD-ROM drive is not detected when I am attempting to install Dapper on a totally new HDD.
GParted could not be used for the same reason ...no CD-ROM drive. I do have CD-ROM at the top
in BIOS. Ubuntu installation screen shows:
[COLOR="Red"]
Loading essential drives
Mounting root file system[/COLOR]

Then it jumps to a black screen which says

[COLOR="Red"]Uncompressing Linux...OK, booting the kernel[/COLOR]

After a long wait the screen turns completely black, i.e. nothing was happening during this time.
Earlier I have installed Breezy, Dapper and Edgy yet somehow can't solve this one. Thanks for help.

---

### Post by louieb on 2007-03-31
> **ububaba said:**
> My CD-ROM drive is not detected when I am attempting to install Dapper on a totally new HDD.

Earlier I have installed Breezy, Dapper and Edgy yet somehow can't solve this one. Thanks for help.
Time to play with cheat codes. I have one PC that boots Knoppix 4 just fine. But when I got Knoppix 5 it did the same thing you talked about. Another PC of mine booted Ubuntu 5 ok, but not Ubuntu 6. 
In both cases I had to give it a boot option. the first one I try is nodma or ide=nodma. 
but here a couple of lists.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Knoppix like Ubuntu is Debian based and these may work to
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by ububaba on 2007-04-02
> **louieb said:**
> Time to play with cheat codes. I have one PC that boots Knoppix 4 just fine. But when I got Knoppix 5 it did the same thing you talked about. Another PC of mine booted Ubuntu 5 ok, but not Ubuntu 6. 
In both cases I had to give it a boot option. the first one I try is nodma or ide=nodma. 
but here a couple of lists.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Knoppix like Ubuntu is Debian based and these may work to
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

While on the installation screen, I pressed F6, was thus able to successfully install Edgy on 
a 320 GB disk. However, ran into another hinder. All choices on the Grub screen returned
the same message,"Error, cylinder exceeds maximum supported by BIOS".  Would anyone 
have an idea how the number of cylinders can be altered. I was not asked for the number 
of partitions. I did see a #12 sda when formating(?) was going on. If and when allowed
should one have the maximum or minimum number of partitions.

For those who know it, this must be extremely easy to solve. Thanks in anticipation.

---

### Post by louieb on 2007-04-02
What you got was GRUB error 18. And it may or may  not an easy one to fix.   Some BIOS's  at boot up can't read past the first 1000 cylinders or so. One way to fix it: created a separate boot partition and make sure its within a 1000 cylinders from the start of the disk. Another way is upgrade your BIOS. [http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6](http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6)
Check the Dual boot link I think Herman has some suggestions.
Or boot the live CD goto Applications>Accessories>Terminal and post the output from sudo fdisk -lh and the maybe I can give you some ideas on how to get around your  BIOS limit

---

### Post by ububaba on 2007-04-04
> **louieb said:**
> What you got was GRUB error 18. And it may or may  not an easy one to fix.   Some BIOS's  at boot up can't read past the first 1000 cylinders or so. One way to fix it: created a separate boot partition and make sure its within a 1000 cylinders from the start of the disk. Another way is upgrade your BIOS. [http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6](http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6)
Check the Dual boot link I think Herman has some suggestions.
Or boot the live CD goto Applications>Accessories>Terminal and post the output from sudo fdisk -lh and the maybe I can give you some ideas on how to get around your  BIOS limit

Read Herman and others. Was trying to solve the problem on my own but have slunk back again, a bit red faced. 
In *recovery mode *if I write [COLOR="Red"]exit[/COLOR] when prompted I get prompted again but repeating this exercise once more I can 
now log normally in GUI. Quite an achievement. The *recovery mode* route has to got rid off. 

As you asked when I tried [COLOR="Red"]sudo fdisk -lh[/COLOR] , unfortunately it was an [COLOR="Red"]invalid option[/COLOR]. This is the result of [COLOR="Red"]sudo fdisk -l[/COLOR]

[COLOR="DarkRed"]

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4159    33399135    f  W95 Ext'd (LBA)
/dev/sdb2   *        4160       10533    51199155    7  HPFS/NTFS
/dev/sdb3           10534       10794     2096482+   7  HPFS/NTFS
/dev/sdb4           10795       16709    47512237+   7  HPFS/NTFS
/dev/sdb5               2        4159    33399103+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        1278    10257502+   f  W95 Ext'd (LBA)
/dev/sdc2   *        1279        5745    35881177+   7  HPFS/NTFS
/dev/sdc3            5746        6006     2096482+   7  HPFS/NTFS
/dev/sdc4            6007       19457   108045157+   7  HPFS/NTFS
/dev/sdc5               2        1278    10257471    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23944   192330148+  83  Linux
/dev/hdb2           23945       24321     3028252+   5  Extended
/dev/hdb5           23945       24321     3028221   83  Linux

[/COLOR]

---

### Post by louieb on 2007-04-04
BTW: I fat fingered should have been sudo fdisk -lu
I** take it that this is a new install on sda**. and you let the installer use the entire disk. It is strange that you can boot into recovery mode but not normally. I would have thought neither would work.  
What I would try  is install again only this time use **manual partitioning**. 
When you get to the first partition screen. Make sure the displayed drive is sda (look in upper right corner). Go ahead and select and delete all the partitions on the drive. Leaving 100% unused space.
Now create 4 partitions for:[LIST=1]
[*]/boot (100 meg is plenty) (format ext2 or ext3)
[*]/ (10 gig is plenty go 15 if you want) (format ext3)
[*]/home (use rest of disk except for 1/2 to 1 gig) (format ext3)
[*]swap (1/2 to 1 gig) (format swap).[/LIST]The next screen is where you tell where to mount the partitions. 
It may have guess right at the mount points for the 4 partitions. There will be some drop down lists on that screen 2 lists for each partition. also there will be a check box asking if you want to format the partition. 
One of the columns will list the partition and look like  /dev/sda1 any way before you leave that screen it should look something like this:
```
 partition        mount point           format box
/dev/sda1        /boot       format box checked      
/dev/sda2        /               format box checked      
/dev/sda3        /home      format box checked
/dev/sda4       swap         format box checked

```
Once you get it looking like this your ready to install. Just go for it and see what happens. It should work.
There may be some other partitions listed, that ok,  just make sure that the format box is unchecked.

I know its a pain but its the easiest way to keep the stuff needed to boot in the first part of the disk. At least you don't have to work around another operating system on that hard drive.. :guitar:

---

### Post by ububaba on 2007-04-04
> **louieb said:**
> BTW: I fat fingered should have been sudo fdisk -lu
I** take it that this is a new install on sda**. and you let the installer use the entire disk. It is strange that you can boot into recovery mode but not normally. I would have thought neither would work.  
What I would try  is install again only this time use **manual partitioning**. 
When you get to the first partition screen. Make sure the displayed drive is sda (look in upper right corner). Go ahead and select and delete all the partitions on the drive. Leaving 100% unused space.
Now create 4 partitions for:[LIST=1]
[*]/boot (100 meg is plenty) (format ext2 or ext3)
[*]/ (10 gig is plenty go 15 if you want) (format ext3)
[*]/home (use rest of disk except for 1/2 to 1 gig) (format ext3)
[*]swap (1/2 to 1 gig) (format swap).[/LIST]The next screen is where you tell where to mount the partitions. 
It may have guess right at the mount points for the 4 partitions. There will be some drop down lists on that screen 2 lists for each partition. also there will be a check box asking if you want to format the partition. 
One of the columns will list the partition and look like  /dev/sda1 any way before you leave that screen it should look something like this:
```
 partition        mount point           format box
/dev/sda1        /boot       format box checked      
/dev/sda2        /               format box checked      
/dev/sda3        /home      format box checked
/dev/sda4       swap         format box checked

```
Once you get it looking like this your ready to install. Just go for it and see what happens. It should work.
There may be some other partitions listed, that ok,  just make sure that the format box is unchecked.

I know its a pain but its the easiest way to keep the stuff needed to boot in the first part of the disk. At least you don't have to work around another operating system on that hard drive.. :guitar:

Now I am in a quandary. The recent data which I sent from my computer was after I
had done a manual partitioning. Not much of a bother doing it again but unfortunately, 
I have all my mail is there in Evolution and no longer on the server. Darn. :(  
I presume it will be completely lost, as formatting seems to be a compulsory requirement. 
You wouldn't know any way around it???

---

### Post by ububaba on 2007-04-04
From my headache, it is becoming yours. I could squeeze all the stuff of two 160gb disks on
one, and then install Edgy on the newly freed 160gb disk. If it is not too risky, there I could 
possibly cut and paste Evolution files from 320gb (present sda) and eventually format this
disk and use it only for storage purposes. My old mail could thus be salvaged.:confused:

---

### Post by louieb on 2007-04-04
Sorry I'm out of things to try. I guess you can always see if there a BIOS upgrade available for your PC.  BTW how full is your 200 gig drive? You could backup your home folder to that drive the restore it after you reformat and reinstall. There are a couple of good threads in the HOW TO section on using TAR to create a compressed backup and use that backup to restore. I've had to do that once when I was getting fsck errors on my home partition and had to reformat it.
Thats one way to save your email and all your other settings. Or I guess you could just live with your crazy way of booting. 
You can use **df -h** to find available space.

Just searched Synaptic for backup and found BackupPC I think i'm going to install it and check it out. Might be easier that TAR.

---

### Post by louieb on 2007-04-04
BackupPC is an 800 pound gorilla. So I just downloaded **sbackup ** and did a backup with it. Looks like it will fill my backup needs very well. I bet it will work for you to backup and restore your email and settings.

---

