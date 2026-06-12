---
title: "need help writing to second hard drive"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-09-27
I have an internal 200 gb hard drive that I have to mount every time i start up Ubuntu, and also I cannot modify or write files to the drive.

I had used the drive with windows, but it was only used for files, mostly music, some tv shows, and my old documents from windows when I installed Ubuntu on my 1st hard drive.  

I would like to keep all my downloads and programs on the 2nd hard drive as my 1st hard drive is only 36.7 gig (raptor), but obviously I can't write to the drive. Again, the 2nd hard drive has never had an operating system on it.

I searched around, and to help anyone trying to help me, I typed 'ls -la /media' in console:

```
alex@alex-desktop:~$ ls -la /media
total 52
drwxr-xr-x  5 root root  4096 2007-09-27 20:51 .
drwxr-xr-x 21 root root  4096 2007-09-06 00:58 ..
dr-xr-xr-x  1 root root 32768 2007-09-02 19:00 apps_dl
lrwxrwxrwx  1 root root     6 2007-09-05 20:28 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-09-05 20:28 cdrom0
lrwxrwxrwx  1 root root     7 2007-09-05 20:28 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-09-05 20:28 floppy0
-rw-r--r--  1 root root    74 2007-09-27 20:51 .hal-mtab
--wxr-x---  1 root root     0 2007-04-15 07:56 .hal-mtab-lock

```

the drive i can't write to and would like to is 'apps_dl'

:) ty for reading

---

### Post by kelnage on 2007-09-27
What happening here is the drive is owned by the "root" user, which means you will be unable to create or modify files on it. I had a similar problem with a hard drive on this computer.

The way I fixed it was to edit /etc/fstab file. If you could post up your existing fstab file, I could suggest the changes you need to make.

An easy way to view the fstab file is by running the following command:

gksu gedit /etc/fstab

---

### Post by llamakc on 2007-09-27
The above answer is better: fix your /etc/fstab so your user can write to the drive.

---

### Post by ijason on 2007-09-27
hey there.

if you've used this HD for windows, it is most likely formatted NTFS. ubuntu has some issues with that file-format, and you need to download and install a special ap to be able to mount a NTFS drive in a way that's writable (do a search for ntfs on here for relevant threads). 

it sounds like your other issue might be that you're having to mount the drive as super user? if that's the case then you'll need to change ownership to whichever user you want to be allowed to access that drive. 

lastly, i believe that you'd be able to mount the drive automatically through the _system>pref>sessions_ tool. i'm not sure, but you might need to give a group permission to mount the drive without having to sudo the command, and then add your account to that group. unfortunately i don't really know the details of how to do that, just that it's the same process you need to go through to allow normal users to mount volumes through truecrypt.

hope this helps!

---

### Post by llamakc on 2007-09-27
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by alwiap on 2007-09-27
thanks for all the replies, here is my 'gksu gedit /etc/fstab' output from terminal:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bdd03183-3c95-43df-9293-c50945a1ac36 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4b9f1315-94a6-43a3-95a7-f7809082101d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

just to clarify, I have never installed windows on this hard drive, just used it as a 2nd hard drive in windows, and hope to do the same in ubuntu.  

cheers!

Edit:   I installed the ntfs-config package and ran the program , and did as I was told but still can not delete/modify files.  :S

---

### Post by alwiap on 2007-09-27
p.s.

with the ntfs-config program, i unmounted the hard drive, then selected it in the program to be mounted at the point, and it said "Sorry, cannot do it. Thanks" or something like that.  ???

---

### Post by alwiap on 2007-09-28
bump!

---

### Post by kelnage on 2007-09-28
Ah, you have to mount the drive manually? That's why it hasn't appeared in the fstab. How do you mount the drive? Do you run a command?

---

### Post by alwiap on 2007-10-03
> **kelnage said:**
> Ah, you have to mount the drive manually? That's why it hasn't appeared in the fstab. How do you mount the drive? Do you run a command?

when i mount the drive, i go to Places > Computer, and I click on the hard drive and I have to enter my password and then it is mounted.

---

### Post by alwiap on 2007-10-03
bump! still having issues -_-

---

### Post by m9ke on 2007-10-03
OK you are seeing two issues, both with your 200 gb hdd:

1-you can't write to the drive
2-you have to mount the drive manually 


Problem #1 is most likely caused by one or both of the following.  If it's *both* then both must be solved before you can write to the drive.
Problem 1 possible causes:
1-you don't have ownership of the drive
2-the drive is formatted in a filesystem only semi-compatible with Ubuntu such as ntfs.

Can we explore possible fixes a bit?  For example, how much data is on your second drive?  How much trouble would it be to copy this data to another location, format the second drive and copy it back?

Let's get problem 1 understood before tackling Prob 2.

---

### Post by m9ke on 2007-10-05
alwiap, did you get this figured out?  

If so you may want to mark it solved.

---

### Post by alwiap on 2007-10-06
> **m9ke said:**
> alwiap, did you get this figured out?  

If so you may want to mark it solved.

Alas I have not, I was away for 2 days, sorry.

However I have a solution that uses your idea, a friend gave me a 500 GB external USB hard drive, so I can back up the drive with what I want to keep (music, videos, and old windows documents such as pictures and text files) that is no more that 125 GB. 

So overnight tonight I will backup my hard drive, and then I can wipe it and I would like to move everything over again, after the drive has been formatted correctly to work with Ubuntu.  Does that make sense?

Thanks for your help.

---

### Post by alwiap on 2007-10-07
bump

---

### Post by m9ke on 2007-10-07
It makes total sense.  

After you back up your data you will need to choose a file system for your 200GB drive.  

When I had the same choice to make I chose ext3 because I knew I'd never put Windows on this box, and it's a journalled file system.    I have moved lots of music created in Windows in .flac format over to my Linux box and everything worked fine.  Also moved over a couple of  Word files over (both with heavy formatting--i.e. two columns, custom tabs) and they worked fine too.

YMMV but my conclusion is that files created on Windows systems can come over to ext3/Ubuntu and be happy there.  Before you choose something different from ext3, make sure you understand and can live without the advantages of a journalled file system.

When you post back let me know what file system you chose.  Also, please say whether or not you added the second drive (what I am getting at here is if the drive has been in your computer for a while, you r BIOS is probably set up OK wrt drive 1 being primary master and your second drive being primary slave.  If you aren't sure about this we need to figure this out before proceeding further.

Cheers,
m9ke

---

### Post by Tibor60 on 2007-10-08
I have some similar problem, but not the same. I have a second internal drive with ext3 fs on it. And I also have to mount it every time. The external USB disk is mounted automaticly without problem, but for this internal I need every time to mount with the root password. I changed the fstab, created a mount point in mnt, and it works fine, but still the USB drive looks better, with the drive icon... how to do the same?

---

### Post by m9ke on 2007-10-08
Tibor60 you might want to check to make sure the owner of the internal drive is you.
Alwiap, I will watch for a post back re your filesystem and history on your second drive.

---

### Post by Chilongola on 2007-10-09
If you do not mind I also have an interest in the solution.  My windows pc just will not boot and  need to remove the slave drive an install it on this pc.  So will be looking forward to how you gt it to work.  My drive also is in ntfs format.

---

### Post by alwiap on 2007-10-09
> **m9ke said:**
> It makes total sense.  

After you back up your data you will need to choose a file system for your 200GB drive.  

When I had the same choice to make I chose ext3 because I knew I'd never put Windows on this box, and it's a journalled file system.    I have moved lots of music created in Windows in .flac format over to my Linux box and everything worked fine.  Also moved over a couple of  Word files over (both with heavy formatting--i.e. two columns, custom tabs) and they worked fine too.

YMMV but my conclusion is that files created on Windows systems can come over to ext3/Ubuntu and be happy there.  Before you choose something different from ext3, make sure you understand and can live without the advantages of a journalled file system.

When you post back let me know what file system you chose.  Also, please say whether or not you added the second drive (what I am getting at here is if the drive has been in your computer for a while, you r BIOS is probably set up OK wrt drive 1 being primary master and your second drive being primary slave.  If you aren't sure about this we need to figure this out before proceeding further.

Cheers,
m9ke

Thanks for the reply,

I have finished backing up the drive and am ready to reformat it, but I have no idea how to even begin to reformat the drive.  I am quite positive however that my 1st drive is primary master and 2nd is primary slave so nothing to worry about there.  I'm fine with choosing ext3, I just have no idea where to begin!  I hope you understand my no-knowingness. :)

---

### Post by m9ke on 2007-10-09
Chilongola, you are welcome to tag along here.  However if you a moving a drive from one computer to another, you may see issues we don't.

alwiap, excellent!  Good to know we are OK first drive as primary master and second as primary slave.  Good choice of filesystems too. 

Once you are absolutely sure all your data is backed up, and that you want to go with ext3, the next step is to format and partition your second drive.  

There is a great how-to at the link below.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I used this guide when I installed my second drive, which is very comparable to what you are doing, and it went almost with out a hitch.  I worked thru the hitches by getting help on this forum, and so I am sure that between the two of us we will succeed.

Would you be comfortable going ahead with the steps in the guide?  I will stay with you in this thread until we complete getting your second drive ready for use.

One caveat:  if you get stuck, or something seems not to work *stop there*.  Let's change one thing at a time, and make sure each step succeeds before going on to the next step.

Sound OK?

---

### Post by alwiap on 2007-10-09
great thanks so much.  i will tackle this monster tommorow which i have off :), but unfortunately i will be away on business for about a week after tommorow, so hopefully i can get it set straight tommorow.  i scanned through the  guide just now and it looks pretty straightforward, if there are any problems i'll let you know asap.  thanks again!

---

### Post by m9ke on 2007-10-10
Sounds good.  I will watch this thread today.  

Let me know how it goes!

ttyl,
m9ke

---

