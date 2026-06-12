---
title: "Resizing partitions and dual boot"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by greeneemer on 2006-07-23
Hi.
I'm dual booting XP & Ubuntu Dapper Drake on my Inspiron 8600c. The size of my HDD is 80 GB.
ATM I'm using 40 GB for XP and 40 GB for Ubuntu, but I want to change this to 65 GB for XP and 15 GB for Ubuntu (and at the same time reinstall Ubuntu).

My plan is to use GParted's LiveCD and remove my ext3 partition. Then, I'll use 25 GB of the extra space to enlarge my NTFS partition (hopefully and probably without losing any data on that partition). Then I'll let Ubuntu's installation create a new ext3 & swap partition in the 15 GB that's left.

Now, here is my question:
Since I dual boot, a Grub loader is in my MBR. (right..?) Will it be harmful for me to remove my ext3 partition which holds Grub itself? I'm concerned that the Grub loader will try to find some files on a partition that does not exist, and then I'm not sure quite what will happen.
If so, is there any other solution to accomplish what I want?
(which again, in short is: enlarge my NTFS partition without losing any data, and shrink & format my ext3 partition)

...or maybe I'm just worrying without a real reason..?

---

### Post by ahaslam on 2006-07-23
All that should work ok. I shouldn't worry about grub, it'll boot xp as normal.

---

### Post by jjstwerff on 2006-07-23
Well.. it's a bit more complicated than the first anwser.

When you remove the linux partition grub will stop to function.
The first code on the MBR will try to access the partition to read the remaining code and that will be impossible after removal of the partition.

But change the partition with a new ubuntu install instead of some other tool. When you install the next version of ubuntu it will create a new grub and that version will list you XP partition normally.

Just make sure that the new ubuntu partitions are created at the end of the free space after removing the old partitions and you can resize the XP partition in due time.

---

### Post by greeneemer on 2006-07-23
Well, the forums have been down for a while now but here's an update for those who care:

I saw Anthony's answer and thought: cool, and went ahead.
As I had feared, and as jjstwerff said some 10 minutes later :), the Grub loader went crazy when it didn't find the partition with Grub itself on (I got Error 22).
Now, this wasn't very hard to solve since all I had to do was to reinstall Ubuntu just as planned and it reinstalled Grub and all went just fine. The resizing went smooth and without any data lost.

The reason, jjstwerff, that I used GParted's LiveCD instead of Ubuntu's installation to resize my NTFS partition is that I read that the older version of ntfsresize in Ubuntu had some problems with resizing NTFS partitions that was not completly defragged. Everywhere I read, people said that it was better to use GParted's LiveCD because it obvisously had the newest version of ntfsresize.

This raises my curiosity.. Let's say that I -for some reason- want to completly remove Ubuntu (or whatever non-Windows OS that houses a boot loader). How do I do that without reinstalling Windows, overwriting the MBR that way?

---

### Post by menawollas on 2006-07-23
This may not be helpful, but its what I am comfortable with.

Essential tools: (non free, unless you know where to look) GDISK (comes with norton ghost - a better version of FDISK (and it may be free). Partition Magic - though if you look at Psychocats, she can recommend a different open source partitioner)

If you reset the MBR (GDISK 1 /MBR or FDISK /MBR) this will let the PC boot from the active primary partition. (GDISK make it very easy to set which partotion you want to be active).

For partitioning, there is no earthly reason why your XP partition should be greater the 10Gb.  STORE YOUR DATA ON A DIFFERENT PARTITION! Keep the OS partitions small, that way you can easily back them up (eg using Ghost). 

So, think about how you want your disk set up. For an 80Gb disk, and example would be 10Gb XP, 10Gb Ubuntu, 30Gb Fat32 (shared) 30Gb NTFS (readable in Ubuntum but writeable in XP). (oops missed the swap, bit anyway, the XP could be the Primary, and everything else logical).

Now, if your XP partition is set to active, it will always boot. However if you have your ubuntu partition set up with grub (which it should be) all the doing a reset MBR would do is remove the link to this. It is easy to restore it if you boot from the Ubunti live Cd, open a console as root, and then type grub. You can then reset grub in the MBR, and you wil multiboot again!

Do a search for reinstall grub - its two line - roor(hdx,y) setup(hdx)

---

### Post by Nothlit on 2006-07-23
> **greeneemer said:**
> This raises my curiosity.. Let's say that I -for some reason- want to completly remove Ubuntu (or whatever non-Windows OS that houses a boot loader). How do I do that without reinstalling Windows, overwriting the MBR that way?

If I understand your question correctly, you're asking what's the easiest way to get back to a "pure" Windows system, delete your Linux partition, and do away with the dual bootloader?  If so, then the best way I know of is to pop in your Windows installation CD, run it in "Recovery Console" mode and use the "fixmbr" utility.  This will essentially rewrite your master boot record with Microsoft's default, without actually touching your Windows installation itself.  Maybe there are other ways of doing this, but that's the way I've always done it and it has worked fine for me.  Here's the Microsoft documentation on that utility: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by greeneemer on 2006-07-24
> **menawollas said:**
> This may not be helpful, but its what I am comfortable with.

Essential tools: (non free, unless you know where to look) GDISK (comes with norton ghost - a better version of FDISK (and it may be free). Partition Magic - though if you look at Psychocats, she can recommend a different open source partitioner)

If you reset the MBR (GDISK 1 /MBR or FDISK /MBR) this will let the PC boot from the active primary partition. (GDISK make it very easy to set which partotion you want to be active).

For partitioning, there is no earthly reason why your XP partition should be greater the 10Gb.  STORE YOUR DATA ON A DIFFERENT PARTITION! Keep the OS partitions small, that way you can easily back them up (eg using Ghost). 

So, think about how you want your disk set up. For an 80Gb disk, and example would be 10Gb XP, 10Gb Ubuntu, 30Gb Fat32 (shared) 30Gb NTFS (readable in Ubuntum but writeable in XP). (oops missed the swap, bit anyway, the XP could be the Primary, and everything else logical).

Now, if your XP partition is set to active, it will always boot. However if you have your ubuntu partition set up with grub (which it should be) all the doing a reset MBR would do is remove the link to this. It is easy to restore it if you boot from the Ubunti live Cd, open a console as root, and then type grub. You can then reset grub in the MBR, and you wil multiboot again!

Do a search for reinstall grub - its two line - roor(hdx,y) setup(hdx)Thanks for your tips, but I have no real need to locally backup any of my files.
Those files I really really don't want to lose, I store externally at my account on my university. (they take daily backups and keep them for two weeks or so)
Private files like photos and such are already burned to a disc.

Thanks for the tips about making a partition active too.
> **Nothlit said:**
> If I understand your question correctly, you're asking what's the easiest way to get back to a "pure" Windows system, delete your Linux partition, and do away with the dual bootloader?  If so, then the best way I know of is to pop in your Windows installation CD, run it in "Recovery Console" mode and use the "fixmbr" utility.  This will essentially rewrite your master boot record with Microsoft's default, without actually touching your Windows installation itself.  Maybe there are other ways of doing this, but that's the way I've always done it and it has worked fine for me.  Here's the Microsoft documentation on that utility: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
Thanks for this! That was just what I was curious about.


Thanks all for the answers!

---

