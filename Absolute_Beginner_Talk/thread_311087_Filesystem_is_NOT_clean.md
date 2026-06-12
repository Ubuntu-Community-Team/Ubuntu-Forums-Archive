---
title: "Filesystem is NOT clean"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by BLTicklemonster on 2006-12-02
Edgy upgraded to feisty on hdd1
clean format and install of Edgy on hda3
when booting to either, I get this:

```
Log of fsck -C -R -A -a 
Sat Dec  2 02:59:57 2006

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 28313 files, 1821896/1918827 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5: 1867 files, 793489/1279551 clusters
Replaying journal..
Trans replayed: mountid 79, transid 217959, desc 6184, len 46, commit 6231, next trans offset 6214
Trans replayed: mountid 79, transid 217960, desc 6232, len 4, commit 6237, next trans offset 6220
Trans replayed: mountid 79, transid 217961, desc 6238, len 7, commit 6246, next trans offset 6229
Trans replayed: mountid 79, transid 217962, desc 6247, len 32, commit 6280, next trans offset 6263
Reiserfs journal '/dev/hdd1' in blocks [18..8211]: 4 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x1641 of format 3.6 with standard journal
Blocks (total/free): 9056624/2201535 by 4096 bytes
Filesystem is NOT clean
Reiserfs super block in block 16 on 0x1641 of format 3.6 with standard journal
Blocks (total/free): 9056624/2201535 by 4096 bytes
Filesystem is NOT clean

Sat Dec  2 03:00:21 2006
---------------
```-

I can boot to edgy, though I have to wait for all of this to show up before proceeding, but if I try to boot to feisty, it stops, and will not let me proceed. I am stuck at the command line, and no matter what I try to do, I can't do anything. If I try to use any command, it says that whatever I try to do is not found. Sudo, command not found, nano, command not found. It's like it doesn't know how to use the programs installed on it.

What happened? Someone set up us the OS. No really, I cleaned dapper off of hda3, and installed edgy on it. I kept a list on paper of what hd was what, and was comparing as I went along to make sure I would not mess anything up. Which is why it's messed up, because when I manually partitioned to choose where to install, it showed my swap in the wrong place, so I put it where it was supposed to be. Which is the only thing I can think of that would have caused this to happen.

Any ideas, based on the information above on how to correct this problem?

*edit:

that up there is from /var/log/fsck/checkfs on edgy

Here it is from hdd1, which is feisty:
```
Log of fsck -C -R -A -a 
Sat Dec  2 02:58:25 2006

fsck 1.40-WIP (02-Oct-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 28313 files, 1821896/1918827 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5: 1867 files, 793489/1279551 clusters
fsck.ext3: Unable to resolve 'UUID=12a80e39-fc16-48f8-b2b6-a935fa4a79b8'

fsck died with exit status 8

Sat Dec  2 02:58:38 2006
----------------
```

---

### Post by BLTicklemonster on 2006-12-02
Whew, never mind. I corrected it by editing fstab.

Seems like all that new garbage mumbo jumbo (mumbuntu jumbuntu?) they use now can mess a thing up.

So I set things back to the old style:

```
Go to post #6 to see the correction that worked :)

```

You will notice I have commented out all the mumbuntu jumbuntu stuff and put all my stuff in at the end in old school style. 

Boots fine, lasts a long time.

And I thought I'd totally forked up. I was at wit's end when I decided to do this. Nothing like fixing it yourself! 

GOD I LOVE THIS STUFF!!!!!! 

***LINUX, THE ULTIMATE TINKER TOY!***

---

### Post by taurus on 2006-12-02
Wait a second!  Your swap partitions should look like these...

```

/dev/hda6   none   swap   sw   0   0
/dev/hdd2   none   swap   sw   0   0

```

---

### Post by BLTicklemonster on 2006-12-02
remarkable. Yet it works.

I'll change those. Thanks Taurus!

---

### Post by taurus on 2006-12-02
You're welcome.

---

### Post by BLTicklemonster on 2006-12-02
Okay, my bad, I had to edit just a wee bit more, it is now this for edgy

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                            0  0  
# /dev/hdd1                                /media/hdd1     reiserfs     notail                              0  2  
# /dev/hda1
#UUID=B44A-18EF                             /media/hda1     vfat         defaults,utf8,umask=007,gid=46      0  1  
# /dev/hda3
UUID=12a80e39-fc16-48f8-b2b6-a935fa4a79b8  /               reiserfs     defaults                            0  1  
# /dev/hda5
#UUID=5CE6-F939                             /media/hda5     vfat         defaults,utf8,umask=007,gid=46      0  1  
# /dev/hdb1
#UUID=C6C49053C4904817                     /media/hdb1     ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  
#UUID=C6C49053C4904817                      /media/hdb1     ntfs-3g      defaults,nls=utf8,umask=007,gid=46  0  1  
# /dev/hdd2
#UUID=cdd1194f-995d-4899-9294-9f17588c73ff  none            swap         sw                                  0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                         0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto                      0  0  
/dev/hda1                                  /media/hda1     vfat         defaults                            0  0  
/dev/hda3                                  /               reiserfs     notail                              0  1  
/dev/hda5                                  /media/hda5     vfat         defaults                            0  0  
/dev/hda6                                  /media/hda6     swap         defaults                            0  0  
/dev/hdb1                                  /media/hdb1     ntfs         defaults                            0  0  
/dev/hdd1                                  /media/hdd1     reiserfs     defaults                            0  0  
/dev/hdd2                                  /media/hdd2     swap         defaults                            0  0 
```


and this for feisty

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc           proc         defaults                            0  0  
# /dev/hdd1                                /media/hdd1     reiserfs     notail                              0  2  
# /dev/hda1
#UUID=B44A-18EF                             /media/hda1     vfat         defaults,utf8,umask=007,gid=46      0  1  
# /dev/hda3
UUID=12a80e39-fc16-48f8-b2b6-a935fa4a79b8   /               reiserfs     defaults                            0  1  
# /dev/hda5
#UUID=5CE6-F939                             /media/hda5     vfat         defaults,utf8,umask=007,gid=46      0  1  
# /dev/hdb1
#UUID=C6C49053C4904817                      /media/hdb1     ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  
#UUID=C6C49053C4904817                      /media/hdb1     ntfs-3g      defaults,nls=utf8,umask=007,gid=46  0  1  
# /dev/hdd2
#UUID=cdd1194f-995d-4899-9294-9f17588c73ff  none            swap         sw                                  0  0  
/dev/hdc                                    /media/cdrom0   udf,iso9660  user,noauto                         0  0  
/dev/                                       /media/floppy0  auto         rw,user,noauto                      0  0  
/dev/hda1                                   /media/hda1     vfat         defaults                            0  0  
/dev/hda3                                   /media/hda3     reiserfs     defaults                            0  0  
/dev/hda5                                   /media/hda5     vfat         defaults                            0  0  
/dev/hda6                                   /none           swap         sw                                  0  0  
/dev/hdb1                                   /media/hdb1     ntfs         defaults                            0  0  
/dev/hdd1                                   /               reiserfs     notail                              0  1  
/dev/hdd2                                   /none           swap         sw                                  0  0  
```


and can now boot to either os.

again, thanks for the swap info, Taurus. 

(you aren't like the dude from sovietinvasionplan.com, are you?)

---

### Post by taurus on 2006-12-02
sovietinvasionplan.com!!!  Not even close...  [-(

---

### Post by BLTicklemonster on 2006-12-02
it's not what it sounds like. you ought to check it out sometime. neat stuff there, mostly random blog thoughts.

---

### Post by headlights on 2008-06-06
I got the same, error like you. I am no expert, tho i am rather sure your fix is no fix. I looks like me just disables the fsck. I bet your filesystem is still not clean.

You just bypass, the uid and so the fsck, That 'mambojambo' is the way the bootloader identiefs the partitions. fsck uses that. by going 'old school; the os boots tho the fsck is skipped. 

I am going to backup my data to a remote server. and run some checks on my disk and the fs.

---

