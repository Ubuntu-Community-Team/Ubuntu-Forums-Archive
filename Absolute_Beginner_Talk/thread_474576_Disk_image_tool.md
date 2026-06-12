---
title: "Disk image tool?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Wynne G Oldman on 2007-06-15
Hi, at the moment I'm running a dual boot system with XP and Feisty 64 bit. I usually back up my HDD by using the GHOST 2003 dos boot diskette and creating an image on my second hdd. I've read somewhere that GHOST has a problem with the partitions Feisty creates. I'm using a 160 gb SATA HDD as my main drive. My first NTFS partition is 80gb and I installed Ubuntu on the rest of the free space. I used the automatic option to install. Can anyone recommend any other backup solution that isn't dependant on installed operating systems (boots form a seperate disk)? Or is there a solution to GHOST's problem?

---

### Post by jhenager on 2007-06-15
Partimage will do the job.
partimage.org

---

### Post by Wynne G Oldman on 2007-06-15
> **jhenager said:**
> Partimage will do the job.
partimage.orgThanks for the reply. Does it create an image of the entire disk, including the NTFS partition, or just single partitions at a time?

---

### Post by edwardLS on 2007-06-15
Another alternative you may want to consider.  I have been using Acronis True Image for about 2 years now, and I am very pleased with it.  It understands the 'ext3' file system which permits me to restore a single file from a Backup Image.  My only complaint is that the 'Restore' function seems to have some problem when used in a system containing a mixture of PATA and SATA drives.
True Image permits you to create bootable 'Rescue Media' to Zip drives, CD-R media and others.

---

### Post by Wynne G Oldman on 2007-06-15
I've just found out that the version of GHOST that I am using does support ext3 after all, so I'm going to stick with it because I've not found anything else that can match it so far. Thanks for your help.

---

### Post by Wynne G Oldman on 2007-06-16
> **Wynne G Oldman said:**
> I've just found out that the version of GHOST that I am using does support ext3 after all, so I'm going to stick with it because I've not found anything else that can match it so far. Thanks for your help.
I take that back. I've just found out the hard way that GHOST 2003 doesn't support this verion of Linux. Anyway, I've got a reliable backup of XP, and now that I've restored that, I'll be installing Feisty 64bit again to dual boot. I'm thinking of using GHOST to do a sector to sector copy as a backup, as both my 160gb SATA drives are identical. Has anyone got a reliable alternative to this backup method?

---

### Post by ocphil on 2007-06-18
Mondo and partimage are excellent and widely used Linux back up tools - but I'm sure they both have a problem with NTFS. I'm looking for a tool myself that can back up NTFS and *nix drives, and haven't found a simple solution yet. At the moment, i'm copying broken NTFS drives using DriveImage on a Bart PE cd ( a windows live cd in essence), and sometimes using Puppy linux or another linux distro cd to copy windows stuff on to a USB caddy or across the network - the live cds can often see files and partitions that even Bart Pe can't find, but I still can't find a simple NTFS imaging solution for linux. I suspect I just haven't looked hard enough : )

---

### Post by bren on 2007-06-18
> **Wynne G Oldman said:**
> Thanks for the reply. Does it create an image of the entire disk, including the NTFS partition, or just single partitions at a time?

Partimage will do either
In addition it will compress resultant iso
In addition it will split iso's into chunks of size you specify (e.g. one DVD worth)
prevoius poster is right partimage doesnt officially support NTFS but partimage wiki (google it) does say 
         * defrag NTFS first x 2
         * if partimage creates iso successfully then will recreate fine
worked for me with all types of fs

bren

---

### Post by ccfjeff on 2007-06-18
There was a thread a few days ago which included some links and ideas on how to clone &/or backup drives.

Here is a link to a section discussing using VMWare to backup over a network:

[http://ubuntuforums.org/showthread.php?p=2838729#post2838729](http://ubuntuforums.org/showthread.php?p=2838729#post2838729)

This one had a link to a page about GParted/Clonezilla LiveCD:
[http://ubuntuforums.org/showthread.php?p=2840610#poststop](http://ubuntuforums.org/showthread.php?p=2840610#poststop)

I haven't figured out how to use it yet, but maybe there are some additional ideas in there that might be of help.

---

### Post by bomanizer on 2007-06-19
Superb,

any hints regarding backing up a XP ntfs partition from a laptop hdd to a USB-hdd? I think there might be some problems with large files and external drives with *nix tools, or...?

Cheers.

---

### Post by bomanizer on 2007-06-19
[http://ubuntuforums.org/showthread.php?p=2740808&highlight=disk+image+usb+hdd#post2740808]("http://ubuntuforums.org/showthread.php?p=2740808&highlight=disk+image+usb+hdd#post2740808")

Nevermind 8-)

---

### Post by hyper_ch on 2007-06-19
I don't do disk image backups....

A re-install for me is quickly done because I keep track of what I need in a script... if a re-install is needed, I reinstall it, then I restore the sources list and the according keys and then I run that script that fetches all software and customization and stuff....

And for the backup of the data I use rSync and hardlinks. That way I make every 6h a full backup of my files and it doesn't use more than 50% over the current space and I have backups for every 6h for a period over 3 months...

---

