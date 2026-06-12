---
title: "Wish my NFTS was FAT32"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by flotsaminthecosmicsea on 2006-11-03
I always wondered what the difference b/t the two was and chose to format my media hard drive as NFTS when I got it. Now I do and want to tun it in to FAT32.

So, how do I copy all of the files I have on that drive to my Ubuntu drive so I can reformat? I have a lot of music and videos which I can access from Nautilus, but when I go to copy and paste, it just won't do it. No error message, no nothing.

I am a total noob to Linux and would really appreciate simplicity here. Maybe an easy to understand guide via a link or a program of some kind would be of much help.

---

### Post by Sef on 2006-11-03
Are you running a dual boot with Windows and Ubuntu?

---

### Post by rccharles on 2006-11-03
> **flotsaminthecosmicsea said:**
> I always wondered what the difference b/t the two was and chose to format my media hard drive as NFTS when I got it. Now I do and want to tun it in to FAT32.

So, how do I copy all of the files I have on that drive to my Ubuntu drive so I can reformat? I have a lot of music and videos which I can access from Nautilus, but when I go to copy and paste, it just won't do it. No error message, no nothing.



There are experimental drivers for making your NTFS partition writable.

This web site will show you how to make the NTFS partition read/read. I do not know if this is the best way to make the NTFS partition read/write.

[http://www.arsgeek.com/?p=675](http://www.arsgeek.com/?p=675)

For more references, see this thread:
[http://www.ubuntuforums.org/showthread.php?t=291703](http://www.ubuntuforums.org/showthread.php?t=291703)

givré's wrote:
	  	

Re: Ntfsmount Install
Quote:
Originally Posted by Sef View Post
Go to Linux-NTFS to read up on installing. Beware! It is beta, so expect to encounter bugs.
There is actually two version of the fuse driver :
- ntfsmount, which is an almost read/write driver, which lake of many feature in write support. [http://www.linux-ntfs.org](http://www.linux-ntfs.org)
- ntfs-3g, improve version of ntfsmount, full read/write support : [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/), actually in beta, but read/write support is stable.


Robert

---

### Post by Bahbuu on 2006-11-03
Are there any ways to change a NTFS drive to a FAT32 drive without destroying the contents in it?

---

### Post by jwbirdsong on 2006-11-03
If you've got  some free space on your hard drives you can  use BOOTiT NG with the procedure found [HERE](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1711634)

FWIW I've used BING for years with great results.

---

### Post by Sef on 2006-11-03
> There are experimental drivers for making your NTFS partition writable.

Experimental means buggy, so you could end up fine, but could lose all your data too.

If you do want to use one, then get [Knoppix]("http://knoppix.com/"), which has [Captive]("http://www.shockfamily.net/cedric/knoppix/#ntfs") on it.

---

### Post by givré on 2006-11-04
Sef, ntfs-3g is not experimental but in beta, that's not the same thing :
[http://lists.debian.org/debian-wnpp/2006/10/msg00323.html](http://lists.debian.org/debian-wnpp/2006/10/msg00323.html).

And the reason why it is still in beta :
> People are keep asking why ntfs-3g isn't marked stable yet, why it's
still
 in beta when for example the stable Captive NTFS crashes and corrupts NTFS
 by running this simple test:

         for i in `seq 1 200` ; do touch $i ; done

 The answer is that, I'd still like to solve some issues described in the
 README file (e.g. transparent unicode handling, fix posix timestamps,
 running my "mission-critical" workstation Linux for at least a week on NTFS
 root (everything being on only NTFS), finish completely with the posix
 conformance, LTP and some other testsuite, etc). Some of the solutions
 aren't trivial, and the constant testing needs quite a lot of time as well.
 To be honest, it's a bit unbelievable how stable the driver performs during
 general use for so many people ...

And Captive is buggy, unreliable and unmaintained since few month. You should not use it, and recommand it.

---

### Post by shador on 2006-11-04
> **Bahbuu said:**
> Are there any ways to change a NTFS drive to a FAT32 drive without destroying the contents in it?

Yup yup. Partition Magic 8 is a WinXP program. And one of it's features is just that. It converts from NTFS to FAT32 and other way around.

---

### Post by mozetti on 2006-11-04
XP also does this natively, I think.

Boot into XP, right-click 'My Computer', select 'Manage' and choose 'Disk Management' from the left-hand pane. Then right-click the partition, and I think the options are in there.

---

### Post by mendingo84 on 2006-11-04
you could download GParted (it's free software), burn it on a CD, boot from the CD and switch from ntfs to fat32. it works just like PartiotionMagik.

---

### Post by givré on 2006-11-04
Xp do nativly fat32 -> ntfs
but not ntfs -> fat32

---

### Post by jcrnan on 2006-11-04
Remember to keep in mind if you are switching to fat32 or using it at all that it has a max filesisze of 4GB. Meaning non of your single files can be over 4GB.

---

### Post by flotsaminthecosmicsea on 2006-11-04
> **jcrnan said:**
> Remember to keep in mind if you are switching to fat32 or using it at all that it has a max filesisze of 4GB. Meaning non of your single files can be over 4GB.

^Is this true? I can't think of any files I currently have that are larger than 4 GB, but it could be a possible drawback to FAT32 I hadn't thought of.

I am only running Linux for the time being. So solutions involving Windows do not help. I value the files on my hard drive very much and do now wish to lose them, so using some experimental program is also not viable.

I do have enough space on other drives to copy the files from the NFTS hard drive and then reformat it. I'd like to do this and need to know how/why Ubuntu won't let me do it.

---

### Post by Efwis on 2006-11-04
The only way to convert your HDD to fat32 from NTFS is to reformat the drive. There is no way for NTFS to be converted back to fat32 after it is made NTFS.

This has been stated by Micro$oft as well as other program manufacturers of 3rd party software.

The reason for this is because it completely rewrites the file structures for NTFS to help prevent hacking, and corruption according to M$.

You said that you have access to your windows files from linux, so you shouldn't have any problem transferring the files to a linux partition.

---

### Post by PriceChild on 2006-11-04
THe claim that PM will convert it back is slightly unbelievable... i've nver heard of it but it could be true.

This on the other hand:> **mendingo84 said:**
> you could download GParted (it's free software), burn it on a CD, boot from the CD and switch from ntfs to fat32. it works just like PartiotionMagik.Is extremely false. Gparted will format the drive if you change it from fat32 to ntfs.

---

### Post by lazyart on 2006-11-04
Cannot convert from NTFS to FAT32.

You'll need to move your data to another drive/partition and reformat.  You can try Partition Magic to resize your current partition smaller and you might have room to move your data over.

Easiest solution-  buy a USB hard drive (a 40 gig goes for about $70) and use it as a holding place, then move your stuff back after formatting.

I have XP and Ubuntu on seperate machines, so NTFS/FAT32 issues are non-existant.  By using a network I can copy back and forth because the host machine handles the translation.  Just another random thought, as I know not everyone has multiple machines.

---

### Post by flotsaminthecosmicsea on 2006-11-04
As I said, I have the space to copy and paste everything on the nfts drive to my Ubuntu drive, but Ubuntu won't do it. No error message, no nothing. I copy the file, paste it to my desktop (or wherever), the machine acts like its busy for a second, and then when it finishes, my desktop looks the same, without the file I wanted to be there.

---

### Post by jwbirdsong on 2006-11-05
> **flotsaminthecosmicsea said:**
> As I said, I have the space to copy and paste everything on the nfts drive to my Ubuntu drive, but Ubuntu won't do it. <snip>

Which is exactly what the link in  post #5 (Bing NG) will do. As Efwis has said You need to copy and data and recreate the partition as a Fat32 then copy all data back.  It is certianly best to do this from "outside" of an OS  by using a partition manipulator such as BING or Partition Magic.  Bing just happens to be my favorite...it's small..fits on floppy if you have one... and is free.

BTW Efwis..Nice to see you here

---

### Post by rccharles on 2006-11-05
> **flotsaminthecosmicsea said:**
> As I said, I have the space to copy and paste everything on the nfts drive to my Ubuntu drive, but Ubuntu won't do it. No error message, no nothing. I copy the file, paste it to my desktop (or wherever), the machine acts like its busy for a second, and then when it finishes, my desktop looks the same, without the file I wanted to be there.

This maybe a permissions problem.  By default, Ubuntu mounts the NTFS partition so that you need to use the root account to access.

To let any user read the data, do the following:


Start a terminal session, by:
Applications > Accessories > Terminal

To see if it is mounted and see who has access, do:
sudo mount

To find the name of the partition, do:
sudo fdisk -l
# note, the l is the lower case letter l.
# this assumes you have one disk and you booted from this disk

# I assume /dev/hda5 is the device name and /media/windows is the
# mount directory.  Yours will vary.

I suggest you unmount the patition:
umount /dev/hda5
# note the missing n.

If you need to create a directory use:
sudo mkdir /media/windows

Make a backup copy of fstab:
cp -i /etc/fstab /etc/fstab.bac

Here is one way of editing:
sudo nano /etc/fstab

and add or change the line
/dev/hda5 /media/windows ntfs nls=utf8,umask=0222 0 0

Change /dev/hda5 as needed. 

Change /media/windows to the mount directory.

Insert or change nls and umask.

now, either reboot or issue the command

sudo mount -a

Robert

---

### Post by rccharles on 2006-11-05
> **lazyart said:**
> Cannot convert from NTFS to FAT32.



While Windows does not allow you to convert from NTFS to Fat32, Partition Manager seems to.  See this site:
[http://www.symantec.com/home_homeoffice/products/features.jsp?pcid=sp&pvid=pm80](http://www.symantec.com/home_homeoffice/products/features.jsp?pcid=sp&pvid=pm80)


This is one of the key features they list:

Converts partitions among FAT, FAT32, and NTFS without losing data


What M$ is saying is that VFAT/FAT32 doesn't store file permission information whereas NTFS does. So when you use Partition Magic to convert NTFS to VFAT, you will loose the permission information.

Robert

---

### Post by flotsaminthecosmicsea on 2006-11-09
Hard drive wasn't mounted. Fixed.

---

