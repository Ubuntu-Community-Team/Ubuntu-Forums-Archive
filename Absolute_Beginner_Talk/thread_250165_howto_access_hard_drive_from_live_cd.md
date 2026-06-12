---
title: "howto access hard drive from live cd"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-03
Hi Ubuntu people,

I'm trying to make a dual head ATI X800 work and it takes a lot of tinkering with the xorg.conf. Every time I screw it up I don't see anything on the screen and the only way I see to get back on track is to reinstall Ubuntu from scratch. I would much rather copy my backed up xorg.conf from my home directory into /etc/X11 and go for a new try. But how can I acess the files on the hard drive when I boot with the live CD? I can see the hard drive but I cannot mount it, it says something about "not a removable storage device". Can anyone help a somewhat dump first day Ubuntu lover here?

Thanks 
Cruz

---

### Post by ispmarin on 2006-09-03
What is the device of your hard drive? It is SATA or IDE? What partition are you using? You can find this doing a 

dmesg

and then search for hda, hdb, or sda, sdb if SATA. With the right device (/dev/sda1, or /dev/hda2, etc), create a directory (or use the /mnt) and mount the hard drive. You can also try (VERY carefully) to do a fdisk on /dev/sda or /dev/hda and look for the right partition that you want to mount. 

OR... much easily, you can boot your system (not the live cd), press CRTL+ALT+F1, go to a terminal, log in, get root(with sudo), and then copy the backup file again on place...

Hope it helps.

---

### Post by Xappe on 2006-09-03
First locate the partition that is your root. Try
```
sudo fdisk -l
```
for that task.

Now, let's say your root partition is hda1, let's mount it:
```
sudo mount -t ext3 -o defaults /dev/hda1 <mountpoint>
```
where <mountpoint> is an empty directory of your choice.

Then you should be able to copy your files around. If you have your /home on a separate partition you have to mount that as well.

---

### Post by dbd on 2006-09-03
Can't you just choose to boot into recovery mode when you muck xorg.conf, and copy the backup from there? (It won't go graphical in recovery mode.)

I know, not the answer to your question, since I'm not certain what to do and not using the live CD, but this should allow you to solve your problem.

If not this might allow you to mount it in live:
First make a directory to mount the hard drive to then type:

mount *partition* *where you want to mount it*

where *partition* is the partition you want to mount

so for example:
mount /dev/hda /home/cruz/root

good luck :)

---

### Post by cajunlibra on 2006-09-03
My question is related and an extension of the original thread.

Originally I started w/ 1 partition with XP Pro on it.  Then I used the 6.06 Live CD to resize and create new partitions.  I now have 
sda1 FAT16   62.72 MB 
sda2 NTFS (XP installed)   39.06GB
sda3 extended 32.67 GB
     sda5  ntfs 9.77GB
     sda6  ntfs 9.77GB
     sda7  ntfs 12.98GB
     sda8  linux-swap  156.86 MB
sda4 ext3 2.73 GB

sda2,5,6,7 all have an error saying "Unable to read the contents of this filesystem! Because of this some operations may be unavailable.  Did you install the correct plugin for this filesystem?"

Ubuntu is installed on sda7.   I'm still learning and some of the guids are a little confusing for me.

I'd like to mount all HDs and be able to access all.

Thanks

PS>  Also, how do I access a linux drive from XP?
I've been trying to mount the other partitions.  They appear to mount fine but I cannot access them.  I've tried chmod 777 for each new directory created and I am denied permissions.  I have read-only access but am unable to read the information that I know is on the XP partition.

---

### Post by Gut Feeling on 2008-06-07
Hi,

I have a Dell Inspiron 1150 onto which I recently clean-installed Ubuntu 8.04 Desktop (no WinXP or any other OS on it). It worked fine for a few days but then got a GRUB Error 17 on bootup. I followed some instructions for creating a GRUB bootable Flashdrive, which only got me as far as another GRUB error, 21.

I would reinstall Ubuntu from scratch again (wiping the HDD in the process), only I'd taken some family pics off a digital camera and put them on and don't really want to lose them if at all possible.

I've given up on the GRUB solution for now and trying to get access to the hard drive instead, via the Live CD. I've tried using the instructions here but having some problems. My primary drive is sda1 and I'm using the command 'sudo mount -t ext3 -o defaults /dev/sda1 recovery' (I've created a /home/ubuntu/recovery folder), but I get the message: "wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so"

If I do dmesg | tail, one of the things it says is "VFS: Can't find ext3 filesystem on dev sda1".

Maybe it's the 'ext3' filesystem thing but I don't know how to resolve this or check what filesystem I do have.

Any help is appreciated, thanks.

---

### Post by chronographer on 2008-06-07
I have a suggestion for the original poster, if you can't boot into the graphical environment, not gnome, no gdm. Try a 'virtual terminal' which you access with crtl + alt + F1,F2...F6 . then you can (assuming you backed up your xorg.conf) "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf" and then restart gdm with "sudo /etc/init.d/gdm restart". This is what I do, you can also tab back and forth from command line to gnome with ctrl + alt + F1 and ctrl + alt + F7 (F7 is usually where gnome is running).

as for mounting hard drives, I would try ls /dev/hd* or ls /dev/sd* and then test mount them with sudo mount /dev/hda4 /mnt/tmp and then if you want it permanent, add it to your fstab "gksu gedit /etc/fstab" um.. RTFM for how to use fstab.

Gut Feeling: I can usually just double click the partitions in the live cd, if you go places:computer all your partitions should show up. Maybe your partition isn't sda1, try doing "ls /dev/sd*"

---

### Post by Gut Feeling on 2008-06-08
Thanks chronographer for the reply.

**If I do 'sudo fdisk -l' I get the following:**
/dev/sda1 (marked as boot): Id=83, Linux
/dev/sda2: Id=5, Extended
/dev/sda5: Id=82, Linux swap / Solaris

If I go to Places>Computer there is only 'CD/DVD drive' and 'Filesystem'. If I go into 'Filesystem' it just seems to be only what the Live CD loads, and not what's actually on the HDD. For example if I go into 'Filesystem/Home' all it has is  'Ubuntu' which looks to be the Live CD boot Home; and if I go into the Boot folder there is no Grub subfolder, just five *generic.* files and one memtest86+.bin file.

I also followed some steps from here:
[http://ubuntuforums.org/showthread.php?t=680486&highlight=access+hard+drive+live+cd&page=2](http://ubuntuforums.org/showthread.php?t=680486&highlight=access+hard+drive+live+cd&page=2)
...and did a **'sudo -fsck -a /dev/sda1'** and got:
"fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1:
The superblock could not be read or does not describe a correct ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running s2fsck with an alternate superblock:
    e2fsck -b 8193 <device>"

---

### Post by chronographer on 2008-06-11
Try gparted from the live CD. (its in System, Admin, Partition Manager I think) It should clear up your partitions... Other than that I am stumped

edit: Did you try that line: e2fsck -b 8193 <device>, like "sudo e2fsck -b 8193 /dev/sda1" or even just 'sda' that may rescue your system...

---

### Post by Gut Feeling on 2008-06-11
> **chronographer said:**
> Try gparted from the live CD. (its in System, Admin, Partition Manager I think) It should clear up your partitions... Other than that I am stumped

edit: Did you try that line: e2fsck -b 8193 <device>, like "sudo e2fsck -b 8193 /dev/sda1" or even just 'sda' that may rescue your system...

Yep tried 'sudo e2fsck -f -b 8193 /dev/sda1' (as well as for all the other superblock backups) but got the same message for all:
"Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?"

Also unmounted /dev/sda1 in case that was the problem but still got the same thing when running the above e2fsck command.

Didn't know about GParted. I opened that and it shows /dev/sda1 as being the boot partition, but Filesystem = 'unknown' and the partition has a yellow triangular exclamation mark icon next to it (the other partitions have a grey 'set of keys' icon). The only option available for partition /dev/sda1 seems to be to format it. If I go to the /dev/sda1 partition's information it says:

Filesystem: unknown
Size: 26.75 GiB
Flags: boot
Path: /dev/sda1
Status: not mounted
Warning:
Unable to detect filesystem! Possible reasons are:
-The filesystem is damaged
-The filesystem is unknown to GParted
-There is no filesystem available (unformatted)

(Unless it's the fact the partition's status is unmounted and needs to be remounted?)

Thanks for trying anyhoo :-)

---

### Post by Victormd on 2008-06-11
If it was working fine and became unbootable, could it be that your HD is messed up(i.e., bad blocks)? Does your BIOS have a HD check utility? If so, I'd run it just to be sure... if not, get the gparted live CD to see if it detects anything out of the ordinary.

edit:
Just saw that you already ran gparted and that the CD shows an unknown fs... I'm not going to say for sure, but chances that your HD died on you are very high...

---

### Post by Victormd on 2008-06-11
> **Gut Feeling said:**
> 
**If I do 'sudo fdisk -l' I get the following:**
/dev/sda1 (marked as boot): Id=83, Linux
/dev/sda2: Id=5, Extended
/dev/sda5: Id=82, Linux swap / Solaris


1. How big is your HD? and how big are sda2+sda5?
2. How much RAM do you have?
You mentioned that gparted recognized the other partitions, so if you want to check and don't mind reinstalling (and depending on how much ram you have), you can combine sda2 and sda5, and install a lighter distro, such as puppy linux or xubuntu (I'd try xubuntu), without swap (or a very small swap partition i.e., 128MB) which you can set up in gparted... and during the install, you'll set another partition as boot, relieving sda1 from that burden.

If in fact your HD died, you won't be able to do this...

If it's a problem with only sda1, then you might be able to troubleshoot better from an installed distro.

---

### Post by Gut Feeling on 2008-06-14
Hi Victormd,

Thanks for reply. Sorry for delay in response, I've been checking this thread every day but didn't realise it'd gone to another page :-$.

1. GParted says 30GB and I'm pretty sure that's correct. sda2 is 1.20GB (or 'GiB' as it says in GParted); sda5 is 1.19GiB.
2. 256MB RAM.

I 'think' it's just a problem with sda1 rather than the whole hdd dying. I'd actually about had enough trying to recover sda1 and was just about to reinstall 8.04 before I saw your post. And since I was about to reinstall/repartition/format anyway, I did some 'recreate file system' command I Googled (mkfs.ext3 /dev/sda1), which did its thing OK but just left me with a 'lost+found' file on the sda1 partition.

I'm just trying your suggestion now. It seems to be putting sda1 aside in its partitioning. Hopefully my mkfs blundering hasn't further sharted it, will let you know.

(Update)
Installed into a new partition, which worked. However I still didn't have permission to access 'lost+found'. There is probably a way to access this but I couldn't be bothered Googling any more solutions to problems I may or may not be able to solve so just reinstalled and partitioned the whole drive, wiping the lot (it gets to a point where the time put into solving is no longer worth it). At least it's working now and it's a good lesson to backup regularly :-|

Thanks for the help anyway Victormd.

---

