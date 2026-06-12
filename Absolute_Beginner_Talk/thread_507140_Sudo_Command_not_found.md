---
title: "Sudo: Command not found"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Quash on 2007-07-22
I am a n00b trying to get ubuntu running.  When I power up the box, I see the ubuntu loading screen.  Afterwards my screen is black.  Several things show up, but most pressing I believe are as follows:

bash sudo: command not found
bash apt-get: command not found

Basically all ubuntu commands show this command not found.  Any ideas on where I can start to repair this ubuntu.  I cannot run the liveCD it freezes up half way.  Any suggestion are much appreciiated.

---

### Post by skymera on 2007-07-22
i had those problems at command line at boot up.

i reinstallled, since it was only 2 days old.

but im sure theres more humane ways to dezl with the situation

---

### Post by nichipet on 2007-07-22
Is this after a fresh install of Ubuntu or did you install new software just before this happened?

Do you get a GRUB screen where you can select an operating system to boot? If you do, try using an Ubuntu option that says something about "safe mode" or "recover mode." See if you can get to a prompt with recover mode.

---

### Post by Quash on 2007-07-22
this happened after a fresh install of ubuntu.  I dont get a GRUB screen unless I have the liveCD in

---

### Post by nichipet on 2007-07-22
Alright, try hitting Esc during the bootup process, early after you start the machine, that should put it into a prompt.

---

### Post by skymera on 2007-07-22
reinsta;; Grub using the Live CD :)

---

### Post by nichipet on 2007-07-22
> **skymera said:**
> reinsta;; Grub using the Live CD :)

Yeah, reinstall will work too, hopefully there is a way to fix the problem without that, though. Someone else had a similar problem before and once they reached the prompt, the missing commands could be reinstalled instead of the entire system.

Here is the thread:

[http://ubuntuforums.org/showthread.php?t=325156](http://ubuntuforums.org/showthread.php?t=325156)

---

### Post by Quash on 2007-07-22
ok i get 3 options  Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+

---

### Post by Quash on 2007-07-22
that thread doesnt help because i command aptitude not found

---

### Post by nichipet on 2007-07-22
Use the second one, the recovery mode. It should take you to a root prompt. From the prompt, there may be a way to reinstall what is missing.

---

### Post by Quash on 2007-07-22
when i run the recovery mode option i get the same series of commands not found also with a bcm43xx_microcode5.fw not available or load failed.  how do i reinstall whats missing?

---

### Post by nichipet on 2007-07-22
> **Quash said:**
> that thread doesnt help because i command aptitude not found

Well, when you get to the prompt, try

```
which aptitude
```

and

```
which apt-get
```

If either of them return a line from /usr/bin, you'll be able to fix the problem.

---

### Post by Quash on 2007-07-22
Thanks btw for helping me out.  when i run those two commands i get root@estridge-laptop:~#

---

### Post by Quash on 2007-07-22
shoot there was a next command that i ran from a search i did that gave me /bin/usr/bin  looking for the thread now, but the next step in that thread never worked for me

---

### Post by Quash on 2007-07-22
I cant find the thread, Im still searching.  Any other ideas on where I could begin?

---

### Post by nichipet on 2007-07-22
If the LiveCD halts halfway through, how did you install Ubuntu?

One option is to get to the root prompt, as you have done, insert the LiveCD, mount it, and then install apt-get from there.

I'm also looking at [http://packages.ubuntu.com/feisty/base/apt](http://packages.ubuntu.com/feisty/base/apt) there may be a way to install apt-get manually and you can then go from there.

---

### Post by Quash on 2007-07-22
Took me a few tries and eventually it got through the install.  How do I mount the liveCD, I think thats a good idea.  Looking at your Link now.

---

### Post by nichipet on 2007-07-22
OK, try this.

Boot into the recovery mode prompt, as you did before. Then

```
which dpkg
```

If that tells you dpkg is in /usr/bin, it can still be fixed. Assuming you have dpkg, here's how to do it.

Insert the LiveCD, it should show up in /media/cdrom

```
ls /media/cdrom
```

should cause some activity for the drive and you should get a list of directories and files. If you don't, look around /media some, it should be in there, if it doesn't, you'll need to manually mount, I'll find the instructions for that or check man mount. If you do have /media/cdrom working...

```
mkdir aptinstall
cd aptinstall
cp /media/cdrom/pool/main/a/apt/* .
dpkg -i apt_0.6.46.4ubuntu10_i386.deb

```

Let's see how all of goes and go from there. If you don't have dkpg, you may need to reinstall and it sounds like your LiveCD has some problems which probably caused not having these commands.

---

### Post by Quash on 2007-07-22
nope the which dpkg shows nothing, so then must i look for another liveCD ??  or can i just reinstall dpkg?

---

### Post by nichipet on 2007-07-22
Was it a burned CD or professionally done CD, such as from a magazine or direct from Ubuntu? If the latter, there shouldn't be any problems with it and a reinstall should sort everything out (make sure you reformat the HD during installation). Before installing, I assume the LiveCD can get you to a desktop with an Install icon. If so, an install should work.

---

### Post by Quash on 2007-07-22
ah ah when  i say cd /media/cdrom, i can get into the cdrom but not through the ls.  it tells me there is no such directory or file as aptinstall

---

### Post by nichipet on 2007-07-22
aptinstall should be created in your root directory where you start the root prompt from. It should not be in /media/cdrom

---

### Post by Quash on 2007-07-22
it was a cd a got from one of my dads business friends who already went on travel.  Im currently downloading the ubuntu from the website 2 hours to go.  the liveCD gets me to the desktop but install halts half way through with an error message that says :

ext3 file system creation in partition #1 of SCSI1 (0,0,0)(sda) failed.

I just wonder how the hell the ubuntu was able to even work the first time i installed it after a few tries

---

### Post by nichipet on 2007-07-22
Try this guide for installing Ubuntu: [http://www.futuredesktop.com/ubuntu7.04.html](http://www.futuredesktop.com/ubuntu7.04.html) Start with Step 3

If it gives you that problem again, something is going wrong when partitioning.

---

### Post by Quash on 2007-07-22
This is the guide that I was using to install ubuntu.  Something wrong when partitioning?  Does that mean my hard drive is now messed up? or am I able to fix this or go around it somehow?

---

### Post by Quash on 2007-07-22
I get a new error that says the attempt to mount a filesystem with type ext3 in SCSI1 (0,0,0) partition #2 (sda) at / failed

again thatnks for taking the time to help me, im not giving up on ubuntu just yet

---

### Post by nichipet on 2007-07-22
As far as I can tell, from searching these forums and Google, that error is related to partitioning. When does it give you this error exactly? Are you getting to the part about partitioning during the install process?

---

### Post by Quash on 2007-07-22
5% done in the partition formatting  part

---

### Post by nichipet on 2007-07-22
See if GParted - [http://gparted.sourceforge.net](http://gparted.sourceforge.net) - is of any help. I think install it and use it while booting from the LiveCD. It looks like you also may need to run through the ndiswrapper process for broadcom before you can download.

---

### Post by Quash on 2007-07-22
Ok im downloading the gparted now also.  You also said to go through the ndiswrapper process before downloading the gparted?  What process are you referring to?

---

### Post by nichipet on 2007-07-22
Don't worry about ndiswrapper if you are already downloading.

---

### Post by Quash on 2007-07-22
ok Ive got it.  Do I restart the comp and boot from the gparted disk?  Instructions are so vague for the noob, sorry.  Again many thanks for helpin me out

---

### Post by nichipet on 2007-07-22
I've never used GParted, so we'll figure this out together. Boot the comp from the livecd and get to the desktop with the Install icon. From there, download/install/run GParted. I think it will work on the hard drive from there, so then double-click the Install icon and follow its instructions.

---

### Post by Quash on 2007-07-22
Ok thanks, Im going to try it now,awwwwwwwwwwwww crap i just got a page, ( im on call at the hospital) , is it ok if I pm you when I come back and if you are free.  Again many thanks. take car

---

### Post by nichipet on 2007-07-22
Sure, that will be fine, but keeping it in the thread will make the full solution available for anyone who searches the forums. I'm subscribed to this thread, so staying here is fine as well.

---

### Post by Quash on 2007-07-23
When I run the gparted it gives me an error saying:

 check the filesystem on dev/sda1 for errors and (if possible) fix them

---

### Post by nichipet on 2007-07-23
Try in a prompt:

```
dosfsck -a -w -v /dev/sda1
```

And search these forums for "check filesystem" (both with and without the quotes). It looks like other people had the same problem, including with GParted. Let me know if anything they suggest works for you.

---

### Post by Quash on 2007-07-23
Thanks for the fast reply,  ok I get 

dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11 12 Mar 2005, FAT 32, LFN
Logical sector size is zero

I found quite a bit of threads, combing through them now

---

### Post by Quash on 2007-07-23
No dice.  I got into some threads that told me to partition using fdisk.  But for some reason after deleting the partitions, when I go to create a new partition the largest I can do is a 4864M.  Ive got a 40GB HD in this dell.  

Any ideas?

---

### Post by nichipet on 2007-07-23
Largest new partition of what type (swap, ext2, ext3, primary, logical, etc.) ? Different types have different limits.

---

### Post by Quash on 2007-07-23
when trying to partition on fdisk it doesnt even give me the option to tell it what type, i just asks me that i want to make a new partition and then i type 1 for the number and then thats it, no other options, perhaps i have to specifiy something after the 1?

---

### Post by Quash on 2007-07-23
hold up i think im getting results via another thread. 

no dice, i get through a few check disk commands and then I cant continue further.  I just tried unmounting my partition in which it gives me an error when i try to create a new partition or try to resize partition

Some other threads talked about unmounting from the terminal however, i get unmount command not found

Alrighty I think I might be getting somewhere when I run this command:  

sudo fsck -fp /dev/sda1

I get that my drive is mounted, yada yada, do I really want to continue,  and I say yes, I get

/dev/sda1: Inode 672915 has illegal blocks
/dev/sda1:  UNEXPECTED INCONSISTENCY; run fsck manually

OK I dunno what im doing but I assumed running manually meant dipping into recovery mode and running fsck, I did that and I get the:

Inode 972915 has illegal blocks clear?  so I say yes....and then I get

Too many illegal blocks in inode 972915.   

Is it now safe to clear the inode.  Im at the point where it says say yes or no

The other thread doesnt get that, so the buck stops here.  Any suggestions?

---

### Post by nichipet on 2007-07-23
The command for unmounting is umount, there is no 'n' after the first 'u'. So, you can try that thread out and see if umount helps. When you run fsck in recovery mode and it asks about Inode, try answering no. It might be asking if the problem is fixed, and if you say no, it may try to repair.

---

### Post by Quash on 2007-07-23
Ok I repaired everything got into it and the same deal happened.  So I booted with the cd.  and said sudo fsck /dev/sda1 in the terminal

and it says fsck.ext3 unable to set superblock flags on /dev/sda1  going back to the unmount thread now

uh oh, now when I run cfdisk /dev/sda I get fatal error cannot open disk drive.  Not quite sure where to look now

---

### Post by nichipet on 2007-07-23
If you have a Windows CD or DVD, maybe try an install of that, just to see how the hard drive holds up and how partitioning goes.

---

### Post by Quash on 2007-07-23
My vista dvd cant do anything, Im currently downloading an XP SP2, I hope I get some luck

---

### Post by Quash on 2007-07-24
I think I give up trying to fix this.  I installed ubuntu, and it works fine then I install ndiswrapper dot deb so I can get wireless as per the dell d800 thread.  and somehow I cant boot up anymore, hard drive becomes corrupted. XP cant partition Vista cant partiition and ubuntu cant partition, none can even reformat.  

 Going to buy a new hard drive now.  Thanks Nichipet for all of your help, much appreciated.  Too bad my ubuntu experience went wrong.  I know Ive heard great things, but it just didnt work for me

UPDATE:::Good news the HD is 40GB, I noticed that when I made the partition 30GB it went further along in formatting and then I got an error, 25GB and error, but 20 GB and I have a formatted XP.  My guess is somehow, the "logical" partition has gone wrong somewhere, once I get into XP I'll use partition magic to see if I can clean up any errors.  Again Thanks for your help, I'll update this again if I figure out whats up

---

### Post by nichipet on 2007-07-24
I'm glad to hear things are going better now. Keep us updated on how it goes. You can have a good Ubuntu system running on just 10-12GB. I'm using less than 9GB and that's with Ubuntu, Ubuntu Studio and KDE installed.

---

