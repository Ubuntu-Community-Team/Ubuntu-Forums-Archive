---
title: "[SOLVED] Where did I screw up in my fstab file?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by weezerisrock on 2007-09-09
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c001773-0061-40c4-8948-b9ae48dfb594 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e05a702e-a7f1-4f23-b760-3460f2bc21be none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb       /ryan-media ext3, umask=0222 0 0
```

that is what I have in there, the last line being the one I added.  I tried following a guide but it was for an ntfs drive and I may have just screwed up.  

I'm trying to get /dev/sdb to automatically mount when I log into linux.

This is the error I get when running "sudo mount -a"

```
mount: unknown filesystem type ''

```

Thanks for any help!

---

### Post by steve.horsley on 2007-09-09
Two errors.
First, /dev/sdb is the entire hard disk. Your NTFS partition is probably the first partition on the disk, so you should probably be saying **/dev/sdb1** instead. 

Second, I don't think there should be a comma after ext3. So I guess the line should be:
/dev/sdb1       /ryan-media ext3   umask=0222 0 0

---

### Post by southernman on 2007-09-09
Start by posting the output of "sudo fdisk -l" then post the output of "blkid"

---

### Post by southernman on 2007-09-09
> **steve.horsley said:**
> Two errors.
First, /dev/sdb is the entire hard disk. Your NTFS partition is probably the first partition on the disk, so you should probably be saying **/dev/sdb1** instead. 

Second, I don't think there should be a comma after ext3. So I guess the line should be:
/dev/sdb1       /ryan-media ext3   umask=0222 0 0
I believe steve, they are saying they followed a guide that was for mounting an NTFS partition, not that they had an NTFS partition to mount. I've been wrong before though. ;)

---

### Post by Fornax-101 on 2007-09-09
sorry, I overlooked some comments

---

### Post by GMachine_24 on 2007-09-09
If it's an ntfs partition you have to substitute ntfs for ext3 as ext3 is a Linux protocol and ntfs is Window$.

==gm

---

### Post by steve.horsley on 2007-09-09
Err, yes. Southernman is right - I may have misunderstod the question. 
Please post the output of the commands
**sudo fdisk -l**
and 
**blkid**
and explain what you are trying to achieve.

---

### Post by weezerisrock on 2007-09-09
Here you guys go.
fdisk -l:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

```

and blkid
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

```

what I'm trying to achieve is I want this full drive to be used for my media (pictures, music, and videos) and its currently not mounting automatically and I would like it to.

thank you for all your help!

---

### Post by alienexplorers on 2007-09-09
Please list your current fstab file.

---

### Post by southernman on 2007-09-09
```
# /dev/sdb1
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 /media/multimedia           	  ext3    defaults        0       2

```
**[edited]** Fixed the above fstab line for use with your output of blkid and added the mount point I suggest below.

1- UUID needs to be replaced with what the command blikid shows to be the UUID for /dev/sdb1* Fixed above code to work for your specific system*
2- The mount point should be a directory you setup in /media. So with that something like...
> sudo mkdir /media/multimedia
Now mount it...
> sudo mount /dev/sdb1 /media/multimedia
Now make it your partition so you can write, edit, delete files as needed...
> sudo chmod 777 -R username:username /media/multimedia ***note:** If you have a lot of files in this partition, it may take a while for the permission changes to be made to all of them. Just saying this so if it takes a while or seems to be hung, you don't panic.

The changes to your fstab won't take place until you reboot, (read: as in auto mounting). **[edited]** Once you have manually mounted the partition you should see your files in the by doing a "ls /media/multimedia".

 For tighter permissions, you can chmod above with 700 if you like. What this does is make it so that only you can read, write and execute files on this drive/partition. 777 means that anyone can do all of that.

---

### Post by weezerisrock on 2007-09-09
Eek!  Ok I think I followed your directions ok...  However now my drive isn't showing up anywhere!  lol.  Ok here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c001773-0061-40c4-8948-b9ae48dfb594 /               ext3    defaults,erro$
# /dev/sda5
UUID=e05a702e-a7f1-4f23-b760-3460f2bc21be none            swap    sw           $
# /dev/sbd1
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 none            ext3    defaults  def$

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

and my blkid:
```
/dev/sda1: UUID="1c001773-0061-40c4-8948-b9ae48dfb594" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e05a702e-a7f1-4f23-b760-3460f2bc21be" TYPE="swap" 
/dev/sdb1: UUID="af6388f7-9507-43cc-8106-daa7d28b5c44" SEC_TYPE="ext2" TYPE="ext3" 

```

Thanks again for all your help!

---

### Post by s[_]spect on 2007-09-09
You havent specified a mount point.
Where you wrote ```
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 none            ext3    defaults  def$
```
you need to change none to your prefered mount point, based on your original post /ryan-media
ie 
```
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 /ryan-media            ext3    defaults  def$
```

---

### Post by weezerisrock on 2007-09-10
hmmm still didn't show up after a reboot, here is the updated fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c001773-0061-40c4-8948-b9ae48dfb594 /               ext3    defaults,erro$
# /dev/sda5
UUID=e05a702e-a7f1-4f23-b760-3460f2bc21be none            swap    sw           $
# /dev/sbd1
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 /ryan-media     ext3    defaults  def$

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by southernman on 2007-09-10
How closely did you follow my directions [here]("http://ubuntuforums.org/showpost.php?p=3339354&postcount=10")?

Did you use the "mkdir" command? If so, what did you call the directory?

If you created a directory as described in my earlier post, you need to replace /ryan-media with that directory. That's telling your system where to mount the partition. If the directory doesn't exist well, natually it can't mount it there.

While you can mount it to /ryan-media, /somelongobsscurename, anything you like really... for the case of keeping things simple and proper, it's best to make all user created mount points in /media. Again, you can call the directory anything you like, just make sure you don't duplicate an existing directory. 

**TIP** - The info you pasted from your fstab file above tells me your not seeing the whole line noted by the [COLOR="Red"]$[/COLOR] at the right side on two of the lines. Drag the window wider with a left mouse click (hold it) and stretch the window until the [COLOR="Red"]$[/COLOR] disappears.

Looks like the only problem with your /dev/sdb1 fstab entry your going to find when you do the above tip, is a duplicate entry for "default." Remove one of them, or it probably won't work still, after getting the mount point entry straightened out.

**TIP 2** - You can also use the command "gksudo gedit /path/to/file" (eg. [COLOR="Red"]gksudo gedit /etc/fstab[/COLOR]) to edit files in a more friendly GUI. Your using "gksudo" in this case because your running a gui application as sudo (eg. the root user). Use this ONLY on an as needed basis!

Once your fstab file is squared away, you can test to see if it works by doing:
> 
sudo mount /dev/sdb1 /media/yournewdirectory
Now you can go to Places > Computer > filesystem > media > yournewdirectory and browse your new mounted partition.

The changes will become permanent (at least until you change it again) after you reboot your system. Once you reboot, there should be an icon on your desktop named "yournewdirectory" and you can also browse the files by going to Places > yournewdirectory.

---

### Post by GMachine_24 on 2007-09-10
I'm surprised anything in the fstab file listed after the # symbol shows up at all - as # basically 'comments out' that line so . . . perhaps removing that symbol would help....

Plus, those are some of the most convoluted lines I've ever seen in an fstab file and the directions are complicated as well for a process that is, really, pretty simple. I  mean... I'm no Linux whiz so perhaps all this stuff you're advising is way over my head but I get drives to partition, mount, etc. all the time with no trouble.



Creating a mount point is simple.

<code>

sudo mkdir /data1

sudo chmod 777 /data1

</code>

The first is to create the mount point and the second is, of course, to enable universal read/write to that file/directory.

To mount the drive manually you:

<code>

sudo mount -t ext3 /dev/hdb1 /data1

</code>

You should now be able to see the /data1 file in your / directory. You can put it in your media directory if you change the mkdir location to **/media/data1**.



Of course you have to edit the fstab file to tell the computer to automatically mount /data1. You can do that by 

<code>

sudo gedit /etc/fstab

</code>

Your fstab file will open and you can insert the command to mount /data1 on boot.

My typical fstab line for a hard drive mount point looks something like this:

<code>

# Device                mountpoint       fstype   options      freq   pass_no

/dev/hdb1              /data1            ext3    defaults        1        2


</code>

Again, don't put a # on the same line and before the /dev/hdb1 etc. or it won't execute that mount.

Save your fstab file and then close it. And you're done.

But, as I said unless I'm missing something, that's pretty much it.



--gm

---

### Post by southernman on 2007-09-10
> **GMachine_24 said:**
> I'm surprised anything in the fstab file listed after the # symbol shows up at all - as # basically 'comments out' that line so . . . perhaps removing that symbol would help....

Plus, those are some of the most convoluted lines I've ever seen in an fstab file and the directions are complicated as well for a process that is, really, pretty simple. I  mean... I'm no Linux whiz so perhaps all this stuff you're advising is way over my head but I get drives to partition, mount, etc. all the time with no trouble.



Creating a mount point is simple.

<code>

sudo mkdir /data1

sudo chmod 777 /data1

</code>

The first is to create the mount point and the second is, of course, to enable universal read/write to that file/directory.

To mount the drive manually you:

<code>

sudo mount -t ext3 /dev/hdb1 /data1

</code>

You should now be able to see the /data1 file in your / directory. You can put it in your media directory if you change the mkdir location to **/media/data1**.



Of course you have to edit the fstab file to tell the computer to automatically mount /data1. You can do that by 

<code>

sudo gedit /etc/fstab

</code>

Your fstab file will open and you can insert the command to mount /data1 on boot.

My typical fstab line for a hard drive mount point looks something like this:

<code>

# Device                mountpoint       fstype   options      freq   pass_no

/dev/hdb1              /data1            ext3    defaults        1        2


</code>

Again, don't put a # on the same line and before the /dev/hdb1 etc. or it won't execute that mount.

Save your fstab file and then close it. And you're done.

But, as I said unless I'm missing something, that's pretty much it.



--gm

Ok point by point then... 

The # sign isn't commenting out the actual mounting commands, it's just a marker so that you can identify easily which hdd partition pertains to the mount point. It isn't rocket science... or is it?

convoluted? Maybe, but that's the structure of the file. Like it or not.

If it was simple, the OP wouldn't be here asking for help. Simple is a relative term... right?

unless a partition isn't a native Linux file system I don't think there is a need to use the "-t ext3"

/ isn't a directory, but a partition

Ubuntu uses UUID's to label partitions by default. That's the norm and suggesting to new users doing otherwise... well, probably isn't the wisest thing to do.

If it's way over your head, do some research on your own and if you can refute my advise then come back and do so... but give links with where you found this stuff! Just because you do things differently and it works for you... well, I'm impressed. :p

Advising someone to run a GUI application with using the gksudo preface isn't very wise.

AFAIK and already stated before, you shouldn't clutter your / partition with various mount points. That's what the /media folder is setup to house (read as: the Ubuntu/Linux file system structure) 

Carry on...

---

### Post by weezerisrock on 2007-09-10
ok so I got to this point:
your post says to do this,
```
sudo chmod -R 777 username:username /media/multimedia
```


and here is what I tried....


```
ryan@gandalf:~$ sudo mount /dev/sdb1 /media/multimedia
Password:
ryan@gandalf:~$ sudo chmod -R 777 ryan:ryan /media/multimedia
chmod: cannot access `ryan:ryan': No such file or directory
ryan@gandalf:~$ sudo chmod -R 777 username:ryan /media/multimedia
chmod: cannot access `username:ryan': No such file or directory
ryan@gandalf:~$ 
```

Thanks for taking so much time to help me. 

I have removed the lines from the fstab while I go thru your step by steps again.  And I have rebooted before doing this too.

---

### Post by GMachine_24 on 2007-09-10
.... yes... by all means... let's meet on the playground after recess .....


look, I was just attempting to point out a few things.... but I'm not going to do a bibliography.

If you don't believe that having a # at the beginning of one of the lines in your fstab file causes the computer to ignore that mount, I invite you to test it yourself. You are wrong. Period.

And, just for the record, the /media location is actually meant for removable drives, such as floppies, DVDs, CD drives, etc. The location you're thinking of for hard drives is /mnt. If you do not believe me, YOU can look it up.

Oh, and... to mount a drive manually before it has been added to fstab, you do, in fact, need to have the -t and ext3 (or other file system) specified in the manual mount command. Which is what I was talking about. I'm surprised, being the obvious super genius that you are, that you didn't realize this.

But enough. I'm sure, eventually, with your exacting precision and perfect instructions the OP will get his computer configured.

For everyone else: Pay no attention to the man behind the curtain.

Peace out.

--gm

---

### Post by weezerisrock on 2007-09-11
Ok so I have now tried both methods and the result appears to be the same.  I can mount the drive manually until I add the info to the fstab and reboot.  Then it appears that my second hard drive disappears.  I can remove the added info from the fstab, reboot and my hard disk shows back up unmounted, from where I can mount it manually again.  :confused:

Here is my fstab after trying GM's method.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c001773-0061-40c4-8948-b9ae48dfb594 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e05a702e-a7f1-4f23-b760-3460f2bc21be none            swap    sw              0       0

# Device mountpoint fstype options freq pass_no

/dev/sdb1       /mnt/media      ext3     defaults        1       2
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by southernman on 2007-09-11
I had the chmod command a little mixed up... so shoot me! ;)

Instead of 
> 
sudo chmod -R 777 username:username /media/multimedia

do 

> sudo chmod 777 -R username:username /media/multimedia

---

### Post by s[_]spect on 2007-09-11
Is this now working for you..?
As for the format of fstab.. you should continue to use the UUID, not /dev/sdb1..
UUID as be required format since Edgy as documented [here]("https://help.ubuntu.com/community/UsingUUID?highlight=%28UUID%29") 

Cheers

---

### Post by weezerisrock on 2007-09-11
I'll try again as soon as I get home.  I was beat last night and ended going to bed early.  This will be the first thing I do when I get home from work.

*crosses fingers*

Thanks everyone!

---

### Post by southernman on 2007-09-11
Hey... I went back to [this post]("http://ubuntuforums.org/showpost.php?p=3339354&postcount=10") and made a few edits so you don't have to jump from page to page.

Changes I made were marked with a bold **edited** tag or by *italic text*.

I'll go back through it once more though and make sure it's right. If you have any questions prior to starting again, let us know. I, with a couple hundred others should be around most of the day. ;)

---

### Post by GMachine_24 on 2007-09-11
I come in peace.

I believe we have failed our friend weezer - for various reasons. Perhaps we should all pull together (in the same direction) and I'm sure we can get his (?) computer up and running.

There is one thing I feel I need to point out, without disputing other items. And that is:

**/ is not a partition**. It is the root directory - I could cite sources for this but, really, do I need to? Things like /dev/hda1 and /dev/sda2 are partitions. / is sort of the mother of all directories .... and all other directories are located in a "tree" stemming from /

But, back to my original thought . . . I think we haven't done a good job helping weezer. I think, for example, the first thing we should have done before advising him how to edit his fstab file would have been to tell/show him how to create a back up of his then-existing fstab. Isn't this what we are all taught to do before we attempt to even open a file with root privileges?

Weezer: For the record, this is how you could have done it:

<code>

user@computername:~$ sudo cp /etc/fstab /etc/fstab.old

</code>

Then check the /etc folder to make sure the copy fstab.old was made.

This, in theory, would have been a good idea.

Also, I use this as my source for most fstab info:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

It's a little dense for newcomers.

Also, why are all of Weezer's drive listed as /dev/sd* devices instead of any /dev/hd*?

How are they connected? And is the boot order in the BIOS set to reflect his hard drive set up?

And, since the point of all of this is to get his media drive mounted and working, and since it's formatted as a Linux drive, I wonder where the drive came from? Did he recently reinstall/install a new OS or did he record his media files while his drive was attached to another Linux box? Or did his media drive previously mount on his current computer (I don't think this is true but . . . ) and quit working or being noticed?

Lastly, putting a # before a command mount line in fstab causes the computer to not execute that mount. I tried it again on two Linux/Ubuntu machines last night with the same result: the drive in the line with the # was not mounted. And, yes, after booting the computer you can manually mount these drives with a simple mount command without specifying -t or the file system.

Would it be ok if Weezer removed the # marks before the mount commands in his fstab file to see if that helps?

--gm

---

### Post by weezerisrock on 2007-09-11
well, I can't answer all of your questions but I can answer two..

The reason my fstab file says sdb instead of hdb is because both disks are SATA drives.
so I'm guessing Serial Disk B as opposed to Hard Disk B?

And I recently installed Linux, this is my second attempt at it, (tried last year but in the end went back to windows, the only reason was for games) and I am finding that things are working out better for me this time around.  The second disk was there when I installed Ubuntu, and I just let the automatic configurator (is that even a word?) do the rest.  When I got in I had my main drive split as filesystem and swap, and my second drive as nothing.  No problem.  That brings us to current.  I have successfully formated and set permissions on the drive and have successfully mounted.  Now I need that process automated.  ( I hope the garbled things that are my thoughts are coherent enough for everyone.)

I appriciate everyone's help!  The mistakes that I make in here only serve to better my knowledge of linux in a way that wouldn't have happened if these mistakes were never made.  I hope to learn more in the process of what you all are showing me.  That is what I love about these forums.  Most of everything I need is ready to be searched for.  And if I can't find it I have people who are completely willing to help me out without looking at me like I'm an idiot.  Those attitudes are the hardest to bear.  So I say again, THANK YOU EVERYONE!  Please keep the info rolling!

P.S. as soon as I get home I will try out the ideas from here and post my results again.

Thankee sais.

---

### Post by southernman on 2007-09-11
Gmachine- as for the fstab file comments reference the two lines below

> 
# /dev/sdb1UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 /media/multimedia           	  ext3    defaults        0       2

In this case, you would be correct without fail. That whole line is commented out and will not be read by the system!
> 
# /dev/sdb1
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 /media/multimedia           	  ext3    defaults        0       2

In this above case, only the line of /dev/sdb1 is commented out. As I said before, it's only used as a reference for future editing and making it easier to locate a partition.

As for the hda vs sda thing... maybe they really have sata or scsi drives, maybe not. I think it depends on the bus system of the motherboard as to exactly how the kernel reports it in related files. I can't explain past that point, but that is what I understand of it myself. It's pretty close though. Thank gosh it's not a hand grenade! ;)

As for backing up system files, and pertaining only to system files (I could be wrong as not tested), I think if you edit a system file the system automatically makes a backup for you by either adding a "~ tilde" to the front of the filename... or by adding a date stamp to the end of the file name. But to the point... you are correct. It should have been a given to add that in our brief howtos.

As for / - It *could* be considered as both a partition and directory I suppose. I think the exacting answer because when you install Linux.. you don't setup a / directory, but a / partition. Now to be more endulging roots home folder (directory) is located at /root... not /

Not brought up by you this round is the little squibble over the location of mounting partitions. While it is a fact that it's totally safe and acceptable to mount them in either /mnt or /media... you were correct, /mnt is actually the place where I've found other more seasoned vets say it *should* be. I mount all mine in /media and it works flawlessly... hence it's what I've suggested in all my other replies to this point.

Now, have we done a good job on weezerisrock's behalf? It really shouldn't have taken 3 pages+? to get this done. I don't put blame on anyone, except myself for the simple fact I had the chmod command turned around. If anyone else takes some of the blame... that's their decision and no need to announce such. It's a mute point anyway.

I've edited my orignal mini howto and verified it works. I think once weezerisrock gets the time later and double/triple checks his directories are setup right things should be just peachy keen.

Now... as long as you don't expect a kiss out of this deal, were kewl... kewl? ;) *very much sarcasm* No harm... No foul - Live and Learn - Que Sara Sara... and all that jazz!

[edited] Dang! I took longer trying to be crafty with my reply than I thought. Well said, weezerisrock! You rock! ;)

---

### Post by GMachine_24 on 2007-09-11
Hey:

Yeah, I kinda figured he had SATA drives but I've learned that sometimes you ask questions you think are obvious and voile all of a sudden the picture is not as you believed. Which is why I was asking questions because I couldn't get a complete picture in my mind.

I was offering the [granted] more simplistic commands using labels instead of the hexidecimal nightmares to try to minimize possible errors. I.E. for me, at any rate, I can get confused about what drive is mounting where - especially if there are several when they are ID'd with those long strings of letteres and numbers - so I use labels (names) until I get things sorted out and then just rewrite the fstab (or whatever) files I need to.

I believe you are correct about Linux creating a 'default' backup~ file for things like fstab and smb.conf. But, I hate to leave things like that to the OS when they are so simple and fast to do on a command line. Besides, it's an old habit. :)

RE:

# /dev/sdb1
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 /media/multimedia ext3 defaults 0 2

I assumed that was on two lines because the terminal window had not been expanded - this is what happens to my fstab and other files when my window is too small and it essentially functions as one line when it is read. I did not know about the "two line" rule but it's obvious now that if you are using the UUID you are not going to be using the /dev/sdb1 to mount the drive. I just never put the # hash mark in the middle of command lines because invariably I screw it up somehow. I will keep it in mind and stand corrected.

Offering that weezer could create a mount point at / was not the wisest choice. I was attempting to say "here is the command you can use" and I added if he wanted to mount it somewhere else he could and I used the path you recommended to the /media folder as an example.

Anyway........ with his last post I now understand things better. I thought he had a drive full of media files already that he had created . . . somehow....on another Linux box. So I was trying to figure out what had changed.

So, pax. But no kisses, thanks.

--gm

---

### Post by weezerisrock on 2007-09-11
Ok I have decided to post an as I go post....

Starting point FSTAB: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c001773-0061-40c4-8948-b9ae48dfb594 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e05a702e-a7f1-4f23-b760-3460f2bc21be none            swap    sw              0       0

# Device mountpoint fstype options freq pass_no


/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
At this point my drive is seen as 111.8 GB volume in "Computer"

This is my BLKID
```
/dev/sda1: UUID="1c001773-0061-40c4-8948-b9ae48dfb594" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e05a702e-a7f1-4f23-b760-3460f2bc21be" TYPE="swap" 
/dev/sdb1: UUID="af6388f7-9507-43cc-8106-daa7d28b5c44" SEC_TYPE="ext2" TYPE="ext3"
```

I now have added the line to the fstab it now looks like this.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c001773-0061-40c4-8948-b9ae48dfb594 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e05a702e-a7f1-4f23-b760-3460f2bc21be none            swap    sw              0       0
# /dev/sdb1
UUID=af6388f7-9507-43cc-8106-daa7d28b5c44 /media/multimedia               ext3    defaults        0       2

# Device mountpoint fstype options freq pass_no


/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
I have now made the directory in the media drive.
```
ryan@gandalf:/media$ dir
cdrom  cdrom0  floppy  floppy0  multimedia

```
I have now successfully used the mount command.
```
ryan@gandalf:/media/multimedia$ dir
lost+found  Music  Pictures

```
And when I try to do the chmod
```
ryan@gandalf:/media/multimedia$ sudo chmod 777 -R ryan:ryan /media/multimedia
chmod: cannot access `ryan:ryan': No such file or directory
ryan@gandalf:/media/multimedia$ sudo chmod 777 -R username:ryan /media/multimedia
chmod: cannot access `username:ryan': No such file or directory
ryan@gandalf:/media/multimedia$ sudo chmod 777 -R username:username /media/multimedia
chmod: cannot access `username:username': No such file or directory

```
(wasn't sure how the username works)

Unfortunately I'll have to finish this after my second job which will be in about 5 hours or so.  See you then!

P.S.  I believe I already have the chmod set, however I can't remember how I did it.  But I can make a directory in this drive.

---

### Post by southernman on 2007-09-11
> **weezerisrock said:**
> 
And when I try to do the chmod
```
ryan@gandalf:/media/multimedia$ sudo chmod 777 -R ryan:ryan /media/multimedia
chmod: cannot access `ryan:ryan': No such file or directory
ryan@gandalf:/media/multimedia$ sudo chmod 777 -R username:ryan /media/multimedia
chmod: cannot access `username:ryan': No such file or directory
ryan@gandalf:/media/multimedia$ sudo chmod 777 -R username:username /media/multimedia
chmod: cannot access `username:username': No such file or directory

```
(wasn't sure how the username works)

Unfortunately I'll have to finish this after my second job which will be in about 5 hours or so.  See you then!

P.S.  I believe I already have the chmod set, however I can't remember how I did it.  But I can make a directory in this drive.
I have no idea what happend... this has always worked for me before. I did a bit of googling and found that this works:

First do
> sudo chown -R ryan:ryan /media/multimedia

Now do
> 
sudo chmod -R 777 /media/multimedia


I guess we didn't get the memo of the change, doing it the way I've suggested before has ALWAYS worked until now! *shakes head in disbelief*
[B]
EDITED - If you can make directories there... you should be good for a reboot and have the drive auto mounting.[/B]

---

### Post by weezerisrock on 2007-09-12
GOOD NEWS!  When I booted my computer back up after getting home from work the drive was present and accounted for!

woot!

I can create, delete and copy to the drive so permissions seem good!

Thank you all so much.

---

### Post by southernman on 2007-09-12
Fantastic weezerisrock! You did good.

Please mark your post as solved... if you don't mind.

---

