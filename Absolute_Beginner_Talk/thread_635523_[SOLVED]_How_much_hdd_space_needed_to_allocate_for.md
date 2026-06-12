---
title: "[SOLVED] How much hdd space needed to allocate for 7.10 install w/vista dual boot?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by TheNorthWaves on 2007-12-08
Yes - I have read the 7.04 tutorial - fwiw has anyone successfully booted 7.10 and vista with vista already installed?

The real question I have is this: since 7.10 has full ntfs read/write capability, but my vista os obviously can't read ext3, it makes the most sense (to me) when setting up a dual-boot to make as small a usable partition as possible for the 7.10 install, and let the rest of the HDD be used for vista + all my files. After all, 7.10 can access the files so it doesn't matter, right? Assuming that I want to install 7.10, open office, and probably a number of other programs - how big of a space should I allocate for the 7.10 install? I have a 120gb hdd in my laptop (something like 110 after ntfs formatting). This is of course assuming that 7.10 needs its own partition to run a dual boot. Sorry - total nOOb. Also, I keep reading about during installation ubuntu will select the largest allocated space or something like that - can I set it to install on the small partition I make for it? 

Thanks,

---

### Post by Crashmaxx on 2007-12-08
I normally use 10GB for my installs, but 5GB will still be more then enough. The minimum is hard to say and it doesn't hurt to have a little more room in case you use it later.

---

### Post by TheNorthWaves on 2007-12-08
I'm under the assumption that during the installation I will be prompted with the option to install on either partition (ie: it's not hidden under 4 layers of menus)? I have never done this before - just want to get my bases covered before I swing the bat.

---

### Post by rsambuca on 2007-12-08
Unless you are installing a bunch of big games, 10GB should be enough.  I use 20 for all of my distros, but none of them is over 10GB.  My Ubuntu partition is only 3.55GB, although I have a separate /home.

Also, just so you know, Vista can read and write to the Ext3 file system with the fs-driver for Windows (just install it in XP compatibility mode).

---

### Post by thelatinist on 2007-12-08
You shouldn't need more than 10 MB.  I strongly recommend a separate shared data partition even for someone single-booting Windows.  That way if anything happens to your Windows installation, you can reinstall without any loss of data.  You also might want to consider a separate home partition.  My recommendation for a dual-boot configuration on, say, a 300 GB HDD is:

20 GB NTFS patition for XP and applications
259 GB NTFS shared data partition
10 GB ext3 partition for /home/
10 GB ext3 partition for /
1 GB swap partition

---

### Post by TheNorthWaves on 2007-12-08
my reply is going to sound quite stupid, but... here goes....

I have a 120gb - 110 after ntfs formatting fyi...

1) I think it's a great idea to have separate partitions for each platform and then a shared partition - but does this necessitate reinstalling vista? I have restore discs. Does this mean that if one of the platforms gets messed up (sans the hdd getting messed up) I can simply restore that particular partiton?

2)what's the swap partition for?

3) what's the deal with having different partitions for / and for /home? (I don't really even know what that is).

Although I am an extreme nOOb, I am really interested in doing the dual-boot in whatever the best way might be - if I reinstall windows, so be it. If I can avoid reinstalling, then that's even better.

---

### Post by Dr Small on 2007-12-08
I installed Gutsy on a 3GB system with VirtualBox. But that doesn't leave any room for expanding.

Dr Small

---

### Post by rsambuca on 2007-12-08
> **TheNorthWaves said:**
> my reply is going to sound quite stupid, but... here goes....

I have a 120gb - 110 after ntfs formatting fyi...

1) I think it's a great idea to have separate partitions for each platform and then a shared partition - but does this necessitate reinstalling vista? I have restore discs. Does this mean that if one of the platforms gets messed up (sans the hdd getting messed up) I can simply restore that particular partiton?

2)what's the swap partition for?

3) what's the deal with having different partitions for / and for /home? (I don't really even know what that is).

Although I am an extreme nOOb, I am really interested in doing the dual-boot in whatever the best way might be - if I reinstall windows, so be it. If I can avoid reinstalling, then that's even better.

You shouldn't have to re-install Vista, but to make room for Ubuntu, it is very important that you defrag Vista a few times, and then "shrink" the partition using the Vista Disk Manager.

The swap is used if your Ram is insufficient.

/ is where all the files and folders are stored (kinda just like a Windows C: drive).  /home is where your personal settings are stored, similar to the My documents.

---

### Post by thelatinist on 2007-12-08
By default the Ubuntu installer will create your / partition and your swap partition for you.  I believe you can choose to create a separate /home partition during installation.  You will need to create your data partition yourself, though.

Personally, I have never had any problems resizing partitions with GParted.  I didn't plan ahead enough when I first installed and had to play with my partitions for a while to get it right (after backing up my data, of course...)

---

### Post by TheNorthWaves on 2007-12-08
I am doing this on a core2duo 2.0ghz lenovo T61 with 2gb 533 ram - so I take it the swap partition is unnecessary. I didn't think I could/should use GParted, because vista has it's own partition maker. Please correct me if I am wrong. I just want to make sure - when I am installing, it will at some point clearly give me the option to install it on whatever free space I want? Or will it just take over and partition whatever unallocated space exists on the hdd? Thank you all for the informative feedback.

---

### Post by rsambuca on 2007-12-08
If you really want the best control over the installation, then shrink the Vista partition using the Disk Manager.  Then use gParted to set up the free space into the exact setup you want.  I would still make a swap, just in case - it's not like you are short of space here.  Then when you install Ubuntu, select Manual Partitioning and point the installer into the partitions that you set up.

---

### Post by richnovil on 2007-12-08
I just used Microsoft Vertual PC 2007 (not some versions have trobbel capturing the mouse) it works nicely :-)

---

### Post by atlfalcons866 on 2007-12-08
dont use gparted to resize the vista version of ntfs. Use the windows one.  I used gparted i messed up my vista partition.

---

### Post by TheNorthWaves on 2007-12-09
ah - thank you both for the clarification on the use of gparted.
I will give this dual boot a try over next weekend. Until then, anyone should feel free to comment about this subject or anything dual-boot related that you think I should know. 
I will check this thread again before doing the setup.

Thanks!

---

### Post by rune0077 on 2007-12-09
I'm dual booting Ubuntu/Vista. There was no need for me to reinstall Vista at all. I used this guide: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) and everything worked fine.

As for Ubuntu communicating with NTFS, don't put to much stock in it. Ubuntu reads files from NFTS rather well, but I have several times tried to save a file in Ubuntu to my Vista-partition, only to find it corrupted when I opened it in Vista (this seems especially true for image files).

---

### Post by TheNorthWaves on 2007-12-09
Does that occur more often than it would if the file were stored on an ext3 partition that vista could access? ie: vista corrupting something for ubuntu. Generally speaking, the types of files I am most concerned about sharing between platforms are excel spreadsheets, word documents, powerpoint presentations, photos and music files. You mentioned images... ultimately as a work computer I am only most concerned about the files of the MS office applications. Windows vista is like an obese person on life support, and I'm just trying to move away from that platform but still maintain its availability when absolutely needed.

---

### Post by rune0077 on 2007-12-09
I'm not sure how it works with ext3 files, since I haven't tried it that way around. For me, it was mostly my photos that got messed up, as well as one or two text files (in OpenOffice format). 

Now, since I have plenty of harddrive space, I've just given 80gb over to my Ubuntu partition, and that way I can store my files there without needing to save it to the NFTS (this way, if I need to transfer the files, I can just copy them so that, even if they're messed up, I still have the original).

---

### Post by AgentZ86 on 2007-12-09
> **TheNorthWaves said:**
> Yes - I have read the 7.04 tutorial - fwiw has anyone successfully booted 7.10 and vista with vista already installed?

The real question I have is this: since 7.10 has full ntfs read/write capability, but my vista os obviously can't read ext3, it makes the most sense (to me) when setting up a dual-boot to make as small a usable partition as possible for the 7.10 install, and let the rest of the HDD be used for vista + all my files. After all, 7.10 can access the files so it doesn't matter, right? Assuming that I want to install 7.10, open office, and probably a number of other programs - how big of a space should I allocate for the 7.10 install? I have a 120gb hdd in my laptop (something like 110 after ntfs formatting). This is of course assuming that 7.10 needs its own partition to run a dual boot. Sorry - total nOOb. Also, I keep reading about during installation ubuntu will select the largest allocated space or something like that - can I set it to install on the small partition I make for it? 

Thanks,

True not much space needed, however if you have already partitioned Vista,restore partitions, and some type of utility partition from the OEM this could create a logistics problem you may have to remove the utility partition and create logical and extended partitions because of the 4 primary partition limit of the hard drive this goes for all the OS's 

if you remove Vista or the restore partition you may not be able to install if your system came with a restore DVD. This is due to the fact the most OEM builders are not giving out re-installation disks anymore only restore DVD's which uses the restore partition and not really a reinstallation disk at all. So if your remove your Vista you can restore from the DVD with restore partition, but if you remove the restore partition you will not be able to reinstall Vista just FYI 
However, if you have an actual re-installation Vista disk or Original Vista installation disk, then this will not be as much of a problem.

I need to order a new compute from Dell to experiment with this subject some more in order to write and actual how to regarding this subject.

Well anyhow just FYI

---

### Post by thelatinist on 2007-12-09
I have never had any problem with Ubuntu failing to write properly to an NTFS partition.  I will note that I never tried writing to my system partition, but only to a separate NTFS-formatted data partition.  As for Vista, I can't really say anything as I've never used it.  If you don't absolutely need Vista for some reason and have an old XP install CD lying around, why not just start over creating an XP-Ubuntu dual boot?

---

### Post by rsambuca on 2007-12-09
I have XP, Vista, and 5 distros on my computer, and I have never had any problems reading and writing to ntfs using a the linux ntfs-3g drivers, nor have I ever had any problems reading and writing to ext3 from XP and Vista using the fs-drivers for Windows.

---

### Post by rune0077 on 2007-12-09
> **rsambuca said:**
> I have XP, Vista, and 5 distros on my computer

Dude, how do you even get past choosing which one you're gonna boot? :)

---

### Post by AgentZ86 on 2007-12-09
> **rune0077 said:**
> Dude, how do you even get past choosing which one you're gonna boot? :)

LOL no crap :guitar:

I've notice your avatar although very different from mine, if you look at them a certain way they also look very similar. Just noticed this today and now wondering where the star trek thing actually derived from. Interesting

---

