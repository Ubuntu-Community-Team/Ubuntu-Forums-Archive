---
title: "[SOLVED] Problem while creating home parition!"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-19
I followed the guide on creating a home partition from here ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)) but something seems to have gone wrong. When I rebooted into Ubuntu Feisty (installed on my computer - i partitioned the drive using a gutsy live cd), everything seems to have reverted back as if Ubuntu were freshly installed. The themes I had installed before are no longer applied and the MS office I had installed with crossover no longer appears under applications. Have I done something wrong or am I supposed to have to do everything again?

EDIT: I forgot to mention that I am able to access files in my home folder without a problem.

---

### Post by intense.ego on 2008-01-19
I wouldn't normally bump so early on but this is an emergency.

---

### Post by mdpalow on 2008-01-19
I quickly scanned the link you posted.

When making a new /home partition it would have deleted your old /home and all the configurations you made. Did you back-up your /home like the instructions gave and then restore it properly?

If you made the back-up, you might have missed something. You should be able to do it all again to see if you get it right this time.

Good luck

---

### Post by intense.ego on 2008-01-19
I followed the steps exactly as they mentioned and copied all the terminals directly from the page (though i changed the partition names to match mine). What seems to be wrong is software installed using crossover (ms office, photoshop 7) and everything that I had customized (gdesklets, conky, background, themes, beryl and xgl, and the taskbars). Also, all the settings in firefox seemed to have disappeard, including bookmarks and rss feeds.

---

### Post by intense.ego on 2008-01-19
Actually, I forgot it but I was a bit confused by one part in the guide an I'm not sure I did it correctly. When I was told to put in this bit of code
```
/dev/hda7 /home ext3 nodev,nosuid 0 2
```
I was uncertain what to do so I just pasted it right in the end of the document. If you do not know what I am talking about, I will post a screenshot later when I boot into the Live CD.

---

### Post by kspringer on 2008-01-19
I moved my /home partition the last time about 6 months ago.  I had the same problems you did and concluded ALL of the files and settings weren't transfered.  In particular, some "dot" files and contents. 

For me, there wasn't any rhyme or reason for what wasn't copied -- only that it was all in the home directory.

If you followed the directions correctly, you still have your original home.  This is good.

I opened the file manager in the original home folder (displaying hidden files)  and another in the new home folder (showing hidden files).
Then I ensured I copied each and every folder/directory and all subfolders to the new one. Then went back and counted/compared files in each folder.  Took awhile.

It did the trick and I recovered my settings.

Good luck.

k

---

### Post by intense.ego on 2008-01-20
The person who wrote the guide on psychocats is a member of these forums. Would it be impolite for me to ask him/her for help through a PM?

---

### Post by frup on 2008-01-20
try this. Take the line you added of fstab, reboot and it should be like it was before. mount the new partition and copy over your /home folder to the intended partition exactly. You need to make sure that all permissions and ownerships in those files are correct too.

If you deleted your old /home folder don't do this though.

---

### Post by intense.ego on 2008-01-20
Sorry, I didn't quite get the first part of what you said (the fstab part). I did the partitioning and moving of files through a Gutsy live cd so I'm not sure how file permissions were handled. Perhaps that is the problem.

---

### Post by frup on 2008-01-20
gksudo gedit /etc/fstab... paste it in here.

---

### Post by intense.ego on 2008-01-20
I am not on my ubuntu computer right now but I'll post the output as soon as I get to it.

---

### Post by frup on 2008-01-20
ok.

Removing that line you added to that file should make ubuntu boot to your old home folder *if* it is still there. If you deleted it you might want to explain more first and read more below.

The part you were confused by may be the problem

> /dev/hda7 /home ext3 nodev,nosuid 0 2

If you copied that word for word it probably isn't correct. you will need to post the output of 

sudo fdisk -l

it will look a little like this:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

It should have a minimum of one extra entry and should help a little in determining what your "/dev/hda7" should in fact be.

---

### Post by intense.ego on 2008-01-20
The ouptut of gksudo gedit /etc/fstab was

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ea0c271f-eff1-41fc-a56b-1d694eba6c35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4fe362bc-f422-4dc9-bacd-f411f5b441dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4 /home ext3 nodev,nosuid 0 2
```

---

### Post by intense.ego on 2008-01-20
> **frup said:**
> ok.

Removing that line you added to that file should make ubuntu boot to your old home folder *if* it is still there. If you deleted it you might want to explain more first and read more below.

The part you were confused by may be the problem



If you copied that word for word it probably isn't correct. you will need to post the output of 

sudo fdisk -l

it will look a little like this:


It should have a minimum of one extra entry and should help a little in determining what your "/dev/hda7" should in fact be.

I didn't copy it word for word - I changed it from hda7 to sda4 because that was the name of the new partition i created. 

I didn't delete the old home folder so that isn't a problem. I don't think I should delete that line right now because I am not running ubuntu off a live cd and that could cause some problems.

---

### Post by frup on 2008-01-20
If you did not delete the old /home folder removing 

/dev/sda4 /home ext3 nodev,nosuid 0 2

from the file, saving and rebooting should allow you access your system just like it was before. You can follow the guide again carefully maybe and double check the permissions, ownerships and files.  Is it possible you left out the hidden files and folders? Press CTRL + H in Nautilus or type ls -al in terminal to see these. Most programs have their configuration files hidden in files and folders that begin with a . (eg /.hidden) inside your home directory

---

### Post by intense.ego on 2008-01-20
> **frup said:**
> If you did not delete the old /home folder removing 

/dev/sda4 /home ext3 nodev,nosuid 0 2

from the file, saving and rebooting should allow you access your system just like it was before. You can follow the guide again carefully maybe and double check the permissions, ownerships and files.  Is it possible you left out the hidden files and folders? Press CTRL + H in Nautilus or type ls -al in terminal to see these. Most programs have their configuration files hidden in files and folders that begin with a . (eg /.hidden) inside your home directory

The guide didn't specify having to show hidden files and folders so I figure that's not the problem. I do believe however, that the permissions could have something to do with the problems. Perhaps all the customized settings were protected and not allowed to copy? Just to clarify: i can delete that line, even when not using the live cd, and no harm will come to my computer? Also, in my fstab file, the line i added is not in line with the other similar lines, could this be a problem? i have PMed the author, aysiu, and hopefully he or she will help me.

---

### Post by intense.ego on 2008-01-20
could it be possible that this guide was created with the use of an older live cd in mind?

---

### Post by frup on 2008-01-20
Yes it was for an older version but much of it remains relatively current.

The fstab file define which file systems are mounted at boot. By removing the entry it will just prevent the new /home partition from being mounted to /home and show your old home folder instead.

It is safe and to be double safe you can back it up:
```

sudo cp /etc/fstab /etc/fstab_backup

```

in terminal you can type ls -al this will give you the permissions, ownerships, sizes etc of all files in the directory. Compare those of sda4 /home and the old /home folder.

---

### Post by intense.ego on 2008-01-20
I deleted the last line from the fstab file but when I rebooted I got an error message saying the home directory i had specified did not exist. It seems as though I deleted something or other even though I was sure I followed the guide step by step.

---

### Post by intense.ego on 2008-01-20
should i just follow the directions from the link in the first post and do the whole recovery procedure?

---

### Post by intense.ego on 2008-01-20
I have just run into some more trouble, while performing the third step of the recovery process I got a message telling me I had run out of disk space. what do i do?

---

### Post by frup on 2008-01-20
:S Ok... You can go back to the fstab we had before then. (add the line again)

So the only problem before was that all the configuration was gone?

---

### Post by intense.ego on 2008-01-20
I could add the line back into fstab but I'd much rather do the whole recovery process so that I can try again. What can I do about the disk space problem?

---

### Post by intense.ego on 2008-01-21
bump, anyone?

---

### Post by intense.ego on 2008-01-21
anyone? this is an emergency

---

### Post by philinux on 2008-01-21
Have you followed the bottom bit of the guide

**What happens if it doesn't work.**

---

### Post by intense.ego on 2008-01-21
I tried the bit at the bottom but I got an error message in the terminal that said that there was not space left (on that partition) and that all the files could not be copied (this came as a result of the third command from the "what happens if it doesn't work" part.

---

### Post by philinux on 2008-01-21
In that case I'd boot the live cd and make some space. Maybe use System monitor to check which partition is full. Maybe your home .Trash and /.Trash need emptying.

Also have a look with 

gksudo nautilus 

Just be careful.

When I did this last Oct I bought a 4gig usb drive and backed up home onto it.

---

### Post by intense.ego on 2008-01-21
A few questions
1) just to make sure, I should use this command with ALT + F2?
2) will reissuing the first two commands cause any errors?

---

### Post by philinux on 2008-01-21
> **intense.ego said:**
> A few questions
1) just to make sure, I should use this command with ALT + F2?
2) will reissuing the first two commands cause any errors?

1. If you mean gksudo nautilus then yes you can or open a terminal and issue the command.

2. You've already done the first 2 commands with no errors, therefore no need to repeat apart from maybe the mount command.

---

### Post by intense.ego on 2008-01-21
I am not at my ubutu computer right now but i will post back as soon as i get to it and have carried out your suggestions.

---

### Post by intense.ego on 2008-01-21
I used gksudo nautilus but I only gain access to the root folder of the live cd and not to the other drives. 

I browsed through the hard drives and found i have three home folder. Two are on the 10gb partition on which ubuntu is installed. One of those two is called "home" and is in a folder called "home backup" (and has all 6.5gb of /home) and the other is called "home backup" and is one a folder called "home" (this one is only 5.5gb - probable because my disk is too full") The other one is called "[my name]" and is one the 38gb partition i wanted to use as my home partition.

What I want to do is delete the 5.5gb /home and be able to copy the original /home (the one on the 10gb partition) to my external hdd for backup. I need root priveleges to do both of those things. I will then remove some files from the remaining /home folder on the 10gb partition to make room for the recovery process. 

This is just a thought but perhaps putting the "[my name]" folder into a folder called "home" would fix my problems. If this is true could someone please show me how to bring up fstab for the whole computer because the method on the first page of this thread only brings the one used for the live cd and the method detailed on the guide brings some a document with nothing on it.

---

### Post by thelatinist on 2008-01-21
If you are still trying to fix this problem by restoring the backup you made in /home_backup to your new /home partition, I suggest the following commands.  Please be aware that the first one *will* delete everything currently in your /home partition, so be sure you follow the directions precisely.  If you don't understand anything, *please ask* before you do it:

```
sudo rm -Rf /home
cd /home_backup/home
sudo tar cpf - * | ( cd /home; sudo tar xfvp -)
```

To explain these commands in detail:

**sudo rm -Rf /home** deletes everything in your home directory (that is, in your case everything on /dev/hda4 which is mounted at /home)

**cd /home_backup** switches to the backup of your home directory you made when you were following psychocat's tutorial.

**sudo tar cfp - * \ ( cd /home; tar xfvp -)** tars everything in the current directory (/home_backup), switches to /home, and untars it into /home without saving an intermediate file.  I put the -v flag on the second tar command so you can see what it is copying and monitor progress.  Using this method will preserve all permissions and symbolic links properly, something which might be important when copying your /home folder.

---

### Post by intense.ego on 2008-01-21
I have a few questions regarding the advice you just gave:

1) Can I do this using a live cd?

2) Will this move the home_backup/home file from the 10gb partition to the 38gb partition or will it just restore the previous /home?

3) Will I have to edit fstab or will it automatically boot /home?

---

### Post by thelatinist on 2008-01-21
> **intense.ego said:**
> I have a few questions regarding the advice you just gave:

1) Can I do this using a live cd?

2) Will this move the home_backup/home file from the 10gb partition to the 38gb partition or will it just restore the previous /home?

3) Will I have to edit fstab or will it automatically boot /home?

1) You could do this using the Live CD if you mount all the partitions and change all the commands to reflect the new locations, but it is not necessary as long as you can boot into Linux still.  Linux will let you completely overwrite your /home directory while it is running (you can actually delete your entire system while it is running and not know the difference until you try to reboot!)

2) I just reread you next-to-last post, and need to change the commands I gave you slightly:```
sudo rm -Rf /home
cd /home_backup**/home**
sudo tar cpf - * | ( cd /home; sudo tar xfvp -)
```

This will move everything in the /home_backup/home folder to your new home partition, assuming that the 38 GB partition is currently mounted at /home.

3) Assuming that your fstab still contains the line ```
/dev/sda4 /home ext3 nodev,nosuid 0 2
``` and /dev/sda4 is the 38 GB partition, you won't have to change fstab at all.

---

### Post by intense.ego on 2008-01-21
I'm sorry to be such trouble but I can't boot into normal ubuntu because I had changed fstab. The reason for this is revealed in some of the previous posts in this thread; basically, ubuntu says there is no /home available to mount.  Because of this, your whole solution won't work. If I could just figure out how to edit fstab for the whole computer (gksudo gedit.... doesn't work) and add in the line once again I would be able to carry out your instructions.

EDIT: 
Just for reference, the 10gb partition is located at /dev/sda2 and the 38gb partition is at /dev/sda4

---

### Post by thelatinist on 2008-01-21
> **intense.ego said:**
> I'm sorry to be such trouble but I can't boot into normal ubuntu because I had changed fstab. The reason for this is revealed in some of the previous posts in this thread; basically, ubuntu says there is no /home available to mount.  Because of this, your whole solution won't work. If I could just figure out how to edit fstab for the whole computer (gksudo gedit.... doesn't work) and add in the line once again I would be able to carry out your instructions.

Okay, that should be fairly easy.  Boot into the Live CD and do the following:

```
sudo mkdir /media/sda2
sudo mkdir /media/sda4
mount /dev/sda2 /media/sda2
mount /dev/sda4 /media/sda4
sudo cp /media/sda2/etc/fstab /media/sda2/etc/fstab.bak
gksudo gedit /media/sda2/etc/fstab
```

Now edit your fstab to read:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# /dev/sda2
UUID=ea0c271f-eff1-41fc-a56b-1d694eba6c35 / ext3 defaults,errors=remount-ro 0 1

# /dev/sda5
UUID=4fe362bc-f422-4dc9-bacd-f411f5b441dd none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

/dev/sda4 /home ext3 nodev,nosuid 0 2
```

Save, exit, reboot and you should be back to where you were.  Then you can try the commands I suggested above to fix your home directory problem.

---

### Post by intense.ego on 2008-01-21
Before i can "sudo cp" the fstab file I need to make room on sda2. How can I just delete home/home_backup on sda2?

---

### Post by thelatinist on 2008-01-21
> **intense.ego said:**
> Before i can "sudo cp" the fstab file I need to make room on sda2. How can I just delete home/home_backup on sda2?

Once you have completed the first four steps, creating mount points and mounting sda1 and sda2, use the following command:

```
sudo rm -Rf /media/sda2/home/home_backup
```

I know, I keep telling you to use the command everyone tells you in their signatures never to use.  But it is actually a very useful command for deleting folders and the files they contain, as long as you only use it on things you are *absolutely sure* you don't need.

---

### Post by intense.ego on 2008-01-21
This is what I have left the fstab as. It is not exactly how you said it should be but because all I did was add the last line.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ea0c271f-eff1-41fc-a56b-1d694eba6c35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4fe362bc-f422-4dc9-bacd-f411f5b441dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4 /home ext3 nodev,nosuid 0 2

```

---

### Post by thelatinist on 2008-01-21
> **intense.ego said:**
> This is what I have left the fstab as. It is not exactly how you said it should be but because all I did was add the last line.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ea0c271f-eff1-41fc-a56b-1d694eba6c35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4fe362bc-f422-4dc9-bacd-f411f5b441dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4 /home ext3 nodev,nosuid 0 2

```

That's fine.  I just deleted extra spaces to make it easier to read.  Did it reboot okay?

---

### Post by intense.ego on 2008-01-21
I have rebooted and I am where i started off this thread. The commands you gave me on the previous page; do i still have to use them all? Can you quote the exact ones I am to use so that there is no confusion. Thanks.

---

### Post by thelatinist on 2008-01-21
> **intense.ego said:**
> I have rebooted and I am where i started off this thread. The commands you gave me on the previous page; do i still have to use them all? Can you quote the exact ones I am to use so that there is no confusion. Thanks.

Here are the commands.  Be sure to type them exactly, spaces are especially important in the last one.

```
sudo rm -Rf /home
**sudo mkdir /home**
cd /home_backup/home
sudo tar cpf - * | ( cd /home; sudo tar xfvp -)
```

You may want to check /home_backup/home to make sure it has a folder with your username in it first.  Just to be sure it's the right folder to use.

Oops!  I forgot one command (in bold above).  If you tried the last command without the second, you probably got an error.

---

### Post by intense.ego on 2008-01-21
Not sure if this changes things, but /home_backup/home is now /home_backup/[my name]

I'm assuming the second line is all that has to be changed.

---

### Post by thelatinist on 2008-01-21
> **intense.ego said:**
> Not sure if this changes things, but /home_backup/home is now /home_backup/[my name]

I'm assuming the second line is all that has to be changed.

Just to be sure of something, please post the output of the following:

```
cd /home_backup/[my name]
ls
```

---

### Post by intense.ego on 2008-01-21
Here is the ouput 

```
alsa_setup.sh
attandskills
conky1
daanish.mp3
darwinia
Darwinia
darwinia-full-1.3.0.sh
darwinia-linux-ita.tar.bz2
Desktop
Documents
downloads
dwhelper
Examples
game
Images
Incomplete
Installers
mount.sh
Music
nautilus-debug-log.txt
rdesktop-1.5.0.tar.gz
Shared
Tay_Zonday_Chocolate_Rain.mp3
Tay_Zonday_FEAT_Mista_Johnson_Cherry_Chocolate_Rain.mp3
The Wire Season 4
tmp
to dl on bt~
unmount.sh
Videos
Will Smith
Wireless Card Troubleshooting
XnView-x86-unknown-linux2.x-static-fc4.tgz

```

---

### Post by thelatinist on 2008-01-21
Excellent!  Now these commands:

```
sudo rm -Rf /home/*
cd /home_backup
sudo tar cpf - * | ( cd /home; sudo tar xfvp -)
```

(Note: I changed the first one slightly, too)

---

### Post by intense.ego on 2008-01-21
what about "sudo mkdir home"?

EDIT: Nevermind, that is what the asterisk was for.

---

### Post by intense.ego on 2008-01-21
I am going to reboot right now but will only post back tomorrow (I need to get some sleep).

---

### Post by thelatinist on 2008-01-21
> **intense.ego said:**
> I am going to reboot right now but will only post back tomorrow (I need to get some sleep).

Okay!  Let us know how it comes out!

---

### Post by intense.ego on 2008-01-22
It works! Everything loads up just as it did before the partition.

On my desktop system monitor it says that the filesystem is 8 out of 10gb is filled. I created a thread a while back and was told that 8gb was more than enough for root. Is there something that was left undeleted? Similarly, my home partition is 7.2gb filled but only 27gb free. This is probably the result of rounding with bytes/bits but is it that big a difference?

Finally, do you know any good guides on how to fresh install gutsy (i have feisty) but still keep all the applications/settings, etc.?

---

### Post by philinux on 2008-01-22
Glad you got sorted I put home on /home last year had a couple of teething troubles with permissions. Nothing like your marathon. Anyway this is what you need now.

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

---

### Post by intense.ego on 2008-01-22
That all sounds good and simple but I have a few questions:

1) will it be the same procedure with gutsy?

2) when it says in step 5 to "download and install feisty," can I just use a live cd or do I click on "upgrade" on the package manager update program?

3) should I save a copy of the sources.list and use that one in the new installation in case some applications are not available from the preset repos?

---

### Post by philinux on 2008-01-22
> **intense.ego said:**
> That all sounds good and simple but I have a few questions:

1) will it be the same procedure with gutsy?

2) when it says in step 5 to "download and install feisty," can I just use a live cd or do I click on "upgrade" on the package manager update program?

3) should I save a copy of the sources.list and use that one in the new installation in case some applications are not available from the preset repos?

Yes it's the same procedure. I used a  usb stick.

2) Ignore this you have the gutsy live cd to install from

3) I copied my sources.list into my home desktop then copied it back after the install. Same with the packages file. i think I backed up my xorg.conf too. Just in case. 

This is the real important bit [COLOR="Red"]> If you have a separate /home partition, mount it at /home DO NOT FORMAT IT[/COLOR]

---

### Post by intense.ego on 2008-01-22
Where is the xorg.conf file. Is it in the home folder as a hidden file? 

The "real important bit" that you mentioned. How do I mount it? Do I use one of those commands like "sudo mount -ext3...." or do I just have to double click on the home partition disk on the computer page?

---

### Post by thelatinist on 2008-01-22
> **intense.ego said:**
> It works! Everything loads up just as it did before the partition.

Told ya it would! ;-)  Glad to hear everything worked out.

> On my desktop system monitor it says that the filesystem is 8 out of 10gb is filled. I created a thread a while back and was told that 8gb was more than enough for root.  Is there something that was left undeleted?

I am guessing that you still have your home partition in /home_backup.  If everything is working fine now, you can do

```
sudo rm -Rf /home_backup
```

to delete it.

> Finally, do you know any good guides on how to fresh install gutsy (i have feisty) but still keep all the applications/settings, etc.?

I suggest you post a separate thread about this issue.  You are much more likely to attract people who are knowledgeable about your question that way.  Then you can mark this thread [Solved] using the thread tools menu at the top of the thread.

---

### Post by intense.ego on 2008-01-22
Thanks, thelatinist. Of all the many helpful people on the ubuntuforums, you are the most helpful and patient i have met. This is what makes me love the ubuntu community.

---

### Post by thelatinist on 2008-01-22
> **intense.ego said:**
> Thanks, thelatinist. Of all the many helpful people on the ubuntuforums, you are the most helpful and patient i have met. This is what makes me love the ubuntu community.

Oh, blushing now.   Thank you very much for the kind words.

---

