---
title: "/home/*username* removed!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by shador on 2007-04-29
I'm quite pissed of right now. When I booted up my ubuntu this morning I got the not so good surprise that my home folder had been deleted. 

Wonderful....fu**ing stupid computer. How the hell can something like that happen?? Stupid question now but does Linux have anything live WinXP's system restore stuff so that I can restore it to a previous point? 

My username folder is GONE and with it my project for school that should be turned in on thursday. 

The folder must have gone somewhere right? Please help me find it Im ****** without my files :(

---

### Post by octoberdan on 2007-04-29
Open up a console and issueing the following commands...

```

ls /home/
sudo updatedb
locate "name of the project file or folder you lost"

```

Then copy and paste all the output to us here? If you have any questions about what I mean, ask away, I can be unclear at times.

---

### Post by engla on 2007-04-29
Did you have /home on a separate partition? Is that partition not mounting right now for some reason?

---

### Post by shador on 2007-04-29
I don't get **** from that command. 

"unable to locate <none> via gethostname()" is the only output. 

Worth to mention is also that the bootup fails hard to. There seems to be a problem when it runs fsck or something liek that. I can only enter the fail safe mode. 

I'm totally screwed right? Dammit, the only time I don't backup **** and something like this happens :/

EDIT: No my /home is not on a seperate partittion.

But the file must have gone somewhere right? How can it delete itself I mean? It su fkin stupid! The last thing I did with the computer was installing fluxbox but i can't see why that has anything to do with it.

---

### Post by kvonb on 2007-04-29
It doesn't look good, apparently ext3 overwrites the deleted file with 0s, but you might be lucky.

First thing is DO NOT MOUNT THE PARTITION.

Boot into Windows for now, and download the system rescue CD from here:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

You need to use a disk sector editor to search the partition for some of the text that was in the file.  You might get lucky, but don't hold your breath.

Although it might not have deleted your home folder, download a thing called "explore2fs".  It is a Windows prog that lets you browse Linux ext2 and also ext3 partitions.

See if you can find anything in /home, if your folder is there, then it's just X that has messed up, and refusing to boot.

Good luck.

---

### Post by Najand on 2007-04-29
There is a bug regarding managing IDE harddisks.
Can you copy/past the output of these commands here:
```

$ sudo fdisk -l
$ cat /etc/fstab

```

---

### Post by shador on 2007-04-29
Well that fdisk thing pretty much solved it all.... 

The problem was that I after the original installation of ubuntu had a empty partition wich I was going to use as a media partition between winXP and ubuntu. When I later on formatted the drive the stupiud ******* ubuntu mounted it at /home for some reason that is far beyond my understanding and thus OVERWRITING my real /home. 

So thank you ubuntu for being so clever to mount a newly formatted partition as /home without 
even noticing me, that's just great. 

It seems like my /home/stefan original folder is gone now unless you guys know a way to restore folders.

EDIT: I searched with slocate but found nothing.

---

### Post by kvonb on 2007-04-29
From:  [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)
[B]
[/B]**Q: How can I recover (undelete) deleted files from my ext3 partition?** Actually, you can't! This is what one of the developers, Andreas Dilger, said about it: [I]In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.[/I]
  *Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.*


[I]A recovery programme:
[/I]

[I][http://e2undel.sourceforge.net/usage.html](http://e2undel.sourceforge.net/usage.html)
[/I]

...and another one:

[http://std.dkuug.dk/keld/readme-salvage.html](http://std.dkuug.dk/keld/readme-salvage.html)

Unfortunately running **any** programme on the target partition, and especially booting from it, probably removed all hopes of you ever getting anything back, especially "updatedb"!

It's a tradeoff for security features, once a file is deleted on an ext3 filesystem, it is gone forever, which is great if you want to thwart certain "law" enforcement agencies or whomever!

If you ever have a file system problem, the first thing to do is unmount the thing and don't do anything to it until you have found more information, as every little thing you do reduces your chances of successful recovery.

---

### Post by Najand on 2007-04-29
Well... First of all watch your language. 
Secondly, during formatting it, you probably didn't notice that gparted (I guess that is the one you used for formatting) has selected the new partition as /home mountpoint. 
Do you have any folder called "home" under "root" filesystem (i.e. /) or under "lost+found"?

P.S. Don't blame ubuntu I think you have seen:
> Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

---

### Post by darkrose on 2007-04-29
if a new partition has been mounted as /home all your old data is still thee and untouched. Just unmount the parttion:
sudo umount /home

now look in home:
ls /home

see your folder?

---

### Post by shador on 2007-04-29
Sorry for the langugage but if a tad frustrated right now. And no I didn't do it in gparted. I formatted in Windows and that's why it was so surprising that it got mounted at /home. 

@darkrose: Nope, didn't work :(

---

### Post by louieb on 2007-04-29
>  EDIT: No my /home is not on a seperate partittion.Must be one hell of a windows program. to format a partition, change your /etc/fstab file, and wipe out all the files in the original home. 

or was it Ubuntu that saw a new partition and said oh it think I'll call it home. and while I'm doing that I'll just get rid of the old home?

Seriously I'd like to see you /etc/fstab. Like knovb said get explore2fs or [http://www.fs-driver.org/](http://www.fs-driver.org/) for windows. If your /home was not on a separate partition it should be on the same partition as the /etc directory. 

Hope your right and did not have a separate /home partition. But it sounds like you did and you reformatted it with your windows program.  In that case try the sysrescue CD. or Like my buddy Fallowell did and said "screw it all I'm moving to Austin"

---

