---
title: "permissions"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-01-26
Hi all! I have the 'hda1' icon on the desktop which was created on install. However, when I double click to open, it opens together with a dialogue box that states I do not have the necessary permissions to view the contents.
Can anyone help me with this.[-o<  Thanks

---

### Post by Jucato on 2006-01-26
Most probably this is due that you only have one partition, where / (root), and /home are both located, so the whole partition would belong to root and you wouldn't be able to access it normally.

Could you post what /etc/fstab contains?

---

### Post by bulldogzerofive on 2006-01-26
Is that your windows partition?

---

### Post by Sbarton on 2006-01-26
Fenyx hope this helps:
# /etc/fstab: static file system information
#
# <file system < mount point>   <type>    <options>    <dump>   <pass>
Proc                 /proc                  proc        defaults         0             0
/dev/hda2        /		           ext 3       defaults, errors=remount &#8211;ro 0  1
/dev/hda5       / home                ext 3       defaults          0             2
/dev/hda1       /media/hda1       ntfs         iocharset=utf8,umask=000  0       0
/dev/hda6       none                  swap       sw                   0             0
/dev/hdc        /media/cdrom0    udf , iso9660 user , noauto   0          0
/dev/hdd        /media/cdrom1    udf , iso9660 user ,noauto    0          0
/dev/fd0         /media/floppy0    auto         rw, user , noauto   0          0

Also here is fdisk reading:
Sudo  fdisk &#8211;l
Device Boot	start       End	Blocks	Id	System
/dev/hda1 *	1	4864         39070048+	7	HPFS/NTFS
/dev/hda2	4685	6080	9767520	83	Linux
/dev/hda3	6081	8181	16876282+	f	W95 Ext&#8217;d (LBA)
/dev/hda5	6081	7296	9767488+	83	Linux
/dev/hda6	7297	7527	1855476	82	Linux swap / Solaris
/dev/hda7	7528	8181	5253233+	b	W95 Fat 32

Sorry but this is the best I can do at present as my Linux machine does not yet have internet connection and I have had to type these copies out.
**bullgogzerofive**: Yes I think if you look at the fdisk and fstab details it may be a little clearer.
Thanks

---

### Post by Sutekh on 2006-01-26
I think ullgogzerofive called it right.  

You probably don't want to allow much access to the windows partition.  As Microsoft doens't tell people how NTFS works, the ways in which Linux accesses and writes (in particular) to NTFS are not reommended.

You should be able to access the partition if you browse using a root session of nautilus, as root is the owner of that partition to stop accidents from happening.  Be careful though.

---

### Post by Mustard on 2006-01-26
I think the line in your /etc/fstab concerning your ntfs partition is misconfigured.  I would try editing it to look like this...

```
/dev/hda1    /media/hda1 ntfs  nls=utf8,umask=0222 0    0
```

Basically the only part you are changing is the umask=0000, to read umask=0222.

You can edit the /etc/fstab file with this command, (you should always make backups when you edit critical files too)

```
sudo gedit /etc/fstab
```

---

### Post by Sutekh on 2006-01-26
Here's something I scooped up from the Gentoo web-site
[QUOTE=Gentoo-Wiki]
umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are not present for the mountpoint. It is an octal number, formed like this:

* character '0': Indicates that this is an octal number, not decimal.
* first digit: owner user permissions
* second digit: owner group permissions
* third digit: world permissions (every other user on the system)

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * -
2 | * - *
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000: [/QUOTE]
As Mustard suggests umask=0222 would make the partition read only (read/execute) for everyone.

---

### Post by Sbarton on 2006-01-27
Many Thanks to everyone who replied with suggestions.I tried a couple of things myself before the replies but caused more problems (my error not ubuntu) so I am going to reinstall. Just adds to my linux experience and learning curve. As Arnie says 'I'll be back'. best wishes.

---

### Post by Mustard on 2006-01-27
Good luck. :)

I ending up reinstalling a few times when I first started in June this year.  I ended up creating two seperate installations on separate hard drives, to protect myself from my experimentation.  I had one install that I never touched until I had proven on my 'experimental' install that I knew what I was doing. :)

---

### Post by Jucato on 2006-01-27
Good luck! Just remember, it's not safe to write to NTFS so Ubuntu makes it a default that you can't access any NTFS partition. You can set the fstab as they mentioned, but it's highly recommended that you set it to read only (hence the umask=0222).

Off-topic: Hehehe! I'm currently reinstalling for the 3rd time myself. Is there sort of a "system restore" (sounds so Windows like) feature/program in Ubuntu? Or something like Norton Ghost or Hard Disk Recovery stuff? So you can safely experiment around and not worry about messing up your beautiful setup. :D

---

### Post by bscbrit on 2006-01-27
I've lost count of the number of re-installs that I have done - but then again I am pretty stupid.  Slackware, Mandrake, FC2/3/4 and now my favourite, Ubuntu.  But the easiest (?) way that I have found to restore a system is to keep my /home and /etc on separate partitions.  I also keep a record in a notebook of all the additional programs that I have installed in addition to the basic installation.  To recover, I install from CD, update from the net, add my extras and the system is back the way it once was and fully up-to-date.  You can use Ghost and similar programs but they update to the snapshot in time which may be many months out-of-date - you will have to update from the internet anyway, and you can guarantee that any settings that you made in /etc will not be on the Ghost backup - or at least mine never are! :D

---

### Post by Jucato on 2006-01-27
oh i see... But, for example, in my case, the initial upgrade after installing is taking up almost the same time as the actual install process. And the update to KDE 3.5 is taking up almost as long. would these updates be saved if I put /etc on a different partition? 

P.S. Sorry for hijacking this thread. I just had to ask... :(

---

### Post by Klaidas on 2006-01-27
I have had the same problem - I couldn't open my windows partition. So I just added a [script "Open as root" ]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2523165") :)

---

### Post by bscbrit on 2006-01-27
Fenyx, this thread is in danger of wandering from 'permissions' to 'how to backup'! but, a quick answer to your question is 'No' because it is configuration data that is kept in /etc (mainly).  The binaries could be in /usr/bin, /sbin or elsewhere.

---

### Post by Sbarton on 2006-01-27
Many thanks for your input everyone. One thing I am pleased about is that you have said you have made other installs. Fortunately this is my test machine so no real damage, but I kick myself for not really thinking it out. Never mind. Now about Restore Fenyx, what I have is this, 2 HDD, I have a clone of the master drive on the slave drive (WINXP +). So I can experiment on the drive with other OS +. If anything goes wrong I simply change drives and reclone (with software, adjusting the jumpers). Having two separate drives is highly recommended for these cicumstances. 'I will be back'.

---

### Post by Sbarton on 2006-01-30
**'I'm back'** and this time an update! I have now reinstalled again, and again it all went easy. I now have my windows (hda1) mounted and able to read from it thanks to advice received here. At the install I did not create a Windows Fat partition to which I could read/write to.What is the procedure after creating the partition in Windows (using 3rd party software) to get this partition up and running in my present Ubuntu setup with the correct permissiond to read/write.
Thanks

---

