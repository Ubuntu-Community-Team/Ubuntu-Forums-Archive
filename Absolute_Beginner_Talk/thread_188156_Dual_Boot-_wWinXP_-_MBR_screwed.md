---
title: "Dual Boot- w/WinXP - MBR screwed"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by MojoWorkin on 2006-06-03
I read another post about fixing MBR in a dual boot situation, but I couldn't find my answer. I can't tell which drive Grub is on, and there are more partitions than I expected to see: I created a FAT32 partition as F:\ Linux for install, and it divided it up into three parts... Linux, Filesystem, and another 6GB partion... ??
I Had/Have WinXP installed on a IDE drive (80GB) I installed Ubuntu on another IDE drive (40GB) using the LiveCD. It wrote the Grub into my WinMBR, which I wasn't intending on. Now, after reboot, I get Error 17 during Grub loading, and can only access my computer via the LiveCD, which I'm on now.
I had/have Acronis True Image, and can't even boot from rescue CD via CD drive, only LiveCD will work. I wanted to use Acronis OSS (OS selector) for switching between OS's.
What I need/want is to remove Grub from Windows installation without having to re-install Windows, fix MBR so I can (at least) boot with Rescue CD and restore from backup I created prior to Ubuntu install, or remove Ubuntu and try again with Windows disk disconnected so MBR won't be comprimised.
Is this possible? This is my first try at Linux, except for last night, toying with LiveCD, so forgive me if I'm asking a redundant question, because I didn't search long enough. I will continue searching and return soon, I'm stuck on this LiveCD for now.
And thank you for any replies to my conundrum.

---

### Post by MetalMusicAddict on 2006-06-03
Do you have a windows cd? If so boot from the cd and choose the repair option when it comes up. It will ask you which windows install to access. Once you log into it you will need to type **fixmbr**. If you do a Google search for **fixmbr** you should get better instructions.

---

### Post by MojoWorkin on 2006-06-03
Thank you soooo much for the quick response.
Yes, grabbin' the Win disk now, and will return asap.
Not sure why I haven't thought of that myself, guess I was dumbfounded with the possible loss of data I was facing.
Once fixmbr does it's "thing", I should disconnect the WinXP HDD and then install Ubuntu? so MBR won't be altered? Am I correct there?
Kudos

---

### Post by catlett on 2006-06-03
[QUOTE=MetalMusicAddict]Do you have a windows cd? If so boot from the cd and choose the repair option when it comes up. It will ask you which windows install to access. Once you log into it you will need to type **fixmbr**. If you do a Google search for **fixmbr** you should get better instructions.[/QUOTE]
Just to elaborate, those directions were right on. If you have an XP install disk (or recovery disk from your computer) put it in and boot to it. The installer will start up and come to a screen with options.
They will be a few lines with options:  type "r" for recovery, hit "enter" to start installation or press "esc" to abort installation.
When you hit r you will get to another prompt. It will identify window installs and ask you which one to enter to perform the recovery. (Most people only have 1 but you may have 2 if there is an automatic recovery partition made) It will prompt "enter the number next to the windows install you want to use for recovery" there will be "1: C windows" listed.
When you enter 1 it will take you to a page with a command prompt. Enter this next command when you are at C:\ ```
fixmbr
``` You will be given a warning prompt that the mbr is to be overwritten and you may not be able to access partitions with another os on it and to type "yes" if you want to proceed.
The MBR will be overwritten I.E. grub will be removed and the windows boot manager will be installed to the mbr. When you reboot windows will start like it did before you installed ubuntu. 
Ubuntu will still be on the other drive so you can then install the boot loader you wanted to use from windows and boot into ubuntu from that.

---

### Post by MojoWorkin on 2006-06-03
Very detailed info, and it worked like a charm......
Check's in the mail... :mrgreen: 
Awesome responses and I am sooo glad that I was still able to use the LiveCD to access Firefox and be able to ask. 
I even called the local "geek' squad here in Denver, and he had no knowledge of Linux, so I was sure I was screwed. (funny how he missed fixmbr as well...)
Thanks a mill and I will try Acronis OSS to see if it will load both, if not, I can still use my Boot Menu in BIOS to choose drive to load.
I am very grateful for the speed in which I was answered, and I'm sure I wasn't the first, (and prolly not the last) to overlook the simple things.
I'm also sure I will be back with more detailed questions as I progress using this new enviroment.
Peace

---

### Post by catlett on 2006-06-03
[QUOTE=MojoWorkin]Very detailed info, and it worked like a charm......
Check's in the mail... :mrgreen: 
Awesome responses and I am sooo glad that I was still able to use the LiveCD to access Firefox and be able to ask. 
I even called the local "geek' squad here in Denver, and he had no knowledge of Linux, so I was sure I was screwed. (funny how he missed fixmbr as well...)
Thanks a mill and I will try Acronis OSS to see if it will load both, if not, I can still use my Boot Menu in BIOS to choose drive to load.
I am very grateful for the speed in which I was answered, and I'm sure I wasn't the first, (and prolly not the last) to overlook the simple things.
I'm also sure I will be back with more detailed questions as I progress using this new enviroment.
Peace[/QUOTE]
Ask all you want. Don't worry if it has been asked before. If I don't have any posts to respond to I might have to talk to my wife.:-D

---

### Post by MojoWorkin on 2006-06-03
Orig. post by catlett:
"If I don't have any posts to respond to I might have to talk to my wife."
Who's that looking over your shoulder reading this?
ROFL...

Ok, now here's a better question:
I fixed the MBR and I can use WinXP, n.p.
Reading Acronis's FAQ's page, I find this:
"I already have Acronis OS Selector installed, and I would like to install Linux on my computer. Where should I install the Linux loader: to MBR or to the boot sector of the partition? Maybe I do not have to install it at all?

Acronis OS Selector does not substitute the Linux loader, so you should install the Linux loader (usually GRUB or Lilo) to the boot sector of the partition you plan to install Linux itself."

Do I need the auxilary install CD (with more detailed options) to do this? or should I simply "fix" the install I have to place Grub where Acronis needs it to be?  
I'm not scared to use command line inputs, but I need a copy of the commands to use. Software programming's not my forte. I'm a hardware guy.
And thanks for having this forum for us "wannabefreeofwinxp's".

---

### Post by linuchsan on 2006-06-03
You can install lilo/grub on the first sector of your linux partition, edit
boot.ini on widows and add your linux partition.

---

### Post by catlett on 2006-06-03
Do you know what partition or drive ubuntu is on? I'm assuming it will be /dev/hdb. Boot into the live cd. Enter ```
sudo fdisk -l
``` To see how your partitions are listed.
You can install grub from inside your ubuntu install. I never did from a live cd but lets try it and see what happens enter ```
sudo grub-install /dev/hdb
``` That is assuming your 40 gb with ubuntu is listed as /dev/hdb when you get the output of fdisk -l.
See what happens. I'm thinking there may be an issue because the drive isn't mounted but we can mount it and try again. But for now run grub-inmstall from withinh the live cd.

---

### Post by MojoWorkin on 2006-06-03
So, I DO need the alternate CD to install Grub where I want? correct?
(copied from another post):
"Use the alternate install cd, install grub on a floppy.

The alternate install cd allows you to pick where you want grub to live. This choice is not available in the Live CD installation by design, and grub is placed on the MBR of the first bootable hard disk."

Then I create a folder on Linux partition, install Grub in it, and show Acronis where to look for boot appl. in said folder... right?

*** sorry I posted as you were catlett...***

---

### Post by catlett on 2006-06-03
There are ways to get a copy of grub from the installer but if this works it will be alot easier.
You already have ubuntu installed correct? If worst came to worst you can run the text mode installer from the alternate cd and choose to install grub to your ubuntu drive and not your windows mbr.
Actually that is what we're trying to do right now. Get your grub on the ubuntu partiton and then point acronis's loader to it

---

### Post by MojoWorkin on 2006-06-03
Ok, in LiveCD now, will try you instructions from last page... brb

---

### Post by MojoWorkin on 2006-06-03
Here's what's listed for the drive I installed Ubuntu on:

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4028    32354878+   c  W95 FAT32 (LBA)
/dev/hdd2   *        4029        4826     6409935   83  Linux
/dev/hdd3            4827        4865      313267+   5  Extended
/dev/hdd5            4827        4865      313236   82  Linux swap / Solaris

I used approx. 80% of the drive (when prompted in LiveCD partition manager) I formatted FAT32 for install of Linux. This left a 6GB 'extra" block unused (hdd2?) so far. (I named the drive: Linux) 
So, it's /dev/hdd1 I need for installing Grub? and the hdd5 is swap? what is hdd3?

---

### Post by catlett on 2006-06-03
I don't know if you have to specify or if it just goes to the front of the drive. I beklieve it goes to the first sector.  As long as that drive is just ubuntu and free space go with```
 sudo grub-install /dev/hdd 
``` See what happens and post if there are errors.

P.S. Just for info the * is where your boot sector is on the drive, but go with the generic first. If needed we will get specific and use /dev/hdd2

---

### Post by MojoWorkin on 2006-06-03
Nope, tried it both ways (hdd, and hdd1) no good yet, but we will figure it out.
ubuntu@ubuntu:~$ sudo grub-install /dev/hdd1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/hdd
Could not find device for /boot: Not found or not a block device.

---

### Post by MojoWorkin on 2006-06-03
I don't mind dnld'n the other alternate CD, if it would be easier. Might take an hour for completion of dnld. But if we have a shot here, I can keep trying things too.
Your call...
btw... hdd2 is the extra space I left out of partion I used for install, it's empty as of now FAT32.
ubuntu@ubuntu:~$ sudo grub-install /dev/hdd2
Could not find device for /boot: Not found or not a block device.

---

### Post by catlett on 2006-06-03
Thats because it is a live cd. Getting the alternate cd and doing a fresh install will definately work. Actually if you just instaled ubuntu and don't have anything valuable on it, it will be faster to run the text mode installer from the alternate cd and choose to put grub on ubuntus partition.
That will put grub on ubuntus boot sector and you can use the acronis to send it to there.
So do you have anything inportant on your ubuntu install?  There are a couple of other things to try but it is just as fast to do a fresh install than to keep trying other methods.
Post what you think and I'm game for whatever you want to do.

---

### Post by MojoWorkin on 2006-06-03
I have nothings at all on it, for when I rebooted from initial install that's when MBR was fooked, and I was at a standstill.
Okeedokee,
Will Dnld the alternate CD and return lata,
I just install Grub, not whole 6.06? or do I re-do the whole thing?
Mucho appreciado for your time catlett

---

### Post by catlett on 2006-06-03
With the old installer (and I'm pretty sure it is the same with dapper, there both text based) you would run the install like normal. Get to the partitioner and choose your ubuntu partitions again. Do the same thing, one for root, one for swap etc. Just choose  "DO NOT FORMAT", save data (it was something like that but the point is you could pick the partition and choose not to format the partition ans in turn save the data)
After the selections you select write changes to disk. It will come up with an error. Just keep hitting continue. Eventually you get to a text menu with about 20 entries.
Scroll down to "install grub bootloader". When you choose grub it goes to another page. It will prompt about any other operating systems found and then ask where you want to install. You can choose the MBR of the first drive, the ubuntu partition/drive or a floppy. After you choose, grub will install. That's it, the installer will finish or send you back to that menu. If you get to trhe menu go down to "abort installation".

P.S. The floppy install is actually a good option as well. That way you just put the floppy in to boot to ubuntu. No need to change the windows boot.ini or use acronis. Or you could do the floppy and when you get inside ubuntu run the earlier command to installl grub to the ubuntu drive and you will have a floppy backup.
Post if there is a problem. If things does't work because it is a newer installer you'll have to run the whole install to get it.

---

### Post by MojoWorkin on 2006-06-03
Dnld'd the Alternate version (x64) and burnt to CD, installed... STOP...
Had errors on CD, rewrote CD, verified, 16 errors in first 10% of disk, md5summer quit responding after 51% complete. (reboot)
Aiight, will dnld another copy and hope it was a corrupted file first time.
If it's my Pioneer DVDRW, then I fooked. It burnt the regular 6.06 image, n.p.
(Using Ashampoo Burning Studio 6)
I had enough for one day, starting over tomorrow.
Thanks for the help today, and see ya next time.

---

### Post by MojoWorkin on 2006-06-04
Downloaded the alternate installer (x64) again, and burnt to CD.
Verified after burn, no errors, verified with md5summer, and same 16 errors appeared in first 10%, another 4 appeared in last 10%.
20 total:
[http://i3.photobucket.com/albums/y99/drwngflies/md5errors.jpg](http://i3.photobucket.com/albums/y99/drwngflies/md5errors.jpg)
Can I install from LiveCD, and have Windows drive unplugged so Ubuntu boot will have to go on Ubuntu drive?
That is the only copy I have without errors.
It installed correctly once, except for MBR issue.

---

### Post by catlett on 2006-06-04
If that is all you have it is possible. Put the ubuntu drive in as master and keep the windows drive disconnected. Let the install run again in it's entirety. Grub will go on the first sector of that drive (grub wiil go where it thinks the mbr for the system is. since the other drive isn't hooked up as master right now grub views the first sector of the ubuntu drive as the mbr and will install there)
After install make the necessary adjustments to the connections to make windows master and ubuntu slave. Then use Acronis ( I don't know the workings of it other than what you mentioned) to boot ubuntu. Just point to grub i.e. the first sector of ubuntus drive with acronis' boot manager and this long process should be resolved:-D

---

### Post by MojoWorkin on 2006-06-04
Well, it worked, but not without trials...
I used the LiveCD, and unplugged the WinXp drive, and set new drive as Master.
Installed Ubuntu 6.06, let it reboot, but received another MBR error.
Shut down system, placed WinXP back as Master, placed Linux drive as Slave, rebooted, but hung at DMI ...
Rebooted using BIOS F12, boot management, chose WinXP drive, booted fine.
Launched Acronis OSS, it showed both WinXP and Linux:
[http://i3.photobucket.com/albums/y99/drwngflies/oss.jpg](http://i3.photobucket.com/albums/y99/drwngflies/oss.jpg)
Thanks for all the advice and help with this "simple" install... :rolleyes: 
Now on to bigger and better problems as I learn this new OS.
Catch 'ya on the flip...
Peace

---

### Post by catlett on 2006-06-04
[QUOTE=MojoWorkin]Well, it worked, but not without trials...
I used the LiveCD, and unplugged the WinXp drive, and set new drive as Master.
Installed Ubuntu 6.06, let it reboot, but received another MBR error.
Shut down system, placed WinXP back as Master, placed Linux drive as Slave, rebooted, but hung at DMI ...
Rebooted using BIOS F12, boot management, chose WinXP drive, booted fine.
Launched Acronis OSS, it showed both WinXP and Linux:
[http://i3.photobucket.com/albums/y99/drwngflies/oss.jpg](http://i3.photobucket.com/albums/y99/drwngflies/oss.jpg)
Thanks for all the advice and help with this "simple" install... :rolleyes: 
Now on to bigger and better problems as I learn this new OS.
Catch 'ya on the flip...
Peace[/QUOTE]
See how easy it can be:^o Glad your up and running. Hopoefully you don't have much more trouble. In case your interested, the last link in my signature "dapper guide", has a step by step run down of how to get your install equipped with the internet, dvd, mp3 essentials. It is very thorough but a little advanced. If you follow it exactly and paste and cut commands it will run fine. You can also search for Automatix or Easy Ubuntu, they are scripts that automate the process, if the guide becomes too difficult.

---

### Post by MojoWorkin on 2006-06-04
One last note, as to Dual Boot issue:
The way I did this left one annoying thing:
I still have to press F12 (boot menu) in BIOS everytime and choose the 80GB WinXP disk so Acronis Boot Loader will launch, then choose which OS to boot.
This works, but isn't exactly right.
If I leave it to "find" the Acronis boot software, it hangs everytime at DMI in BIOS, and I have to power off to resume as above.
I chose the 100% available space, when I partitioned the drive, using the LiveCD, (2.1GB, leaving 35Gb unused) and now, after updates were dnld, it says i'm at 95% used disk.
Should I remove this install and give it more room? Seems 2.1 GB ain't enought for any future installs or updates. I'm thinking I should I start over and choose 50% (of 40GB disk, 37.2 available)? Also, I couldn't "drop" any files in the remaining FAT32 partition from WinXp side, and return to Ubuntu and "see' them.
I did manage to mount the extra space on FAt32 drive, but I had to format it first in Linux and virtual FAT, which erased data.
What am I missing again? Is my Alzheimers acting up?

EDIT***
And, I think I found why it screwed up MBR the first time:
When I partition form within WinXP, Acronis Disk Director 10 leaves a portion of drive unallocated in FRONT of each Logical drive, (where the boot is saved?) giving it a wrong read when first accessed.
Only the Local Drive (C:\) has this space at end of drive. Does this make sense?
[http://i3.photobucket.com/albums/y99/drwngflies/drives.jpg](http://i3.photobucket.com/albums/y99/drwngflies/drives.jpg)

---

### Post by catlett on 2006-06-04
I don't know anything about acronis but I think your assumption is right. The MBR is right up front. I wonder if acronis does this on purpose. Erases the mbr so only it's application controls booting. It could be a way of acronis "safeguarding" the mbr from other OSs during installation. If an install rewrote the mbr then acronis wouldn't control booting any more. Maybe it removes that possibility by keeping the MBR unallocated. I'm just guessing but in the beginning I was trying Partition Magic's "Boot Magic" and that was  a concern of the application. It would say that a new install of linux might overwrite the mbr and Boot Magic would be inaccessable until you used there boot floppies.
Anyways if you only have 2.1gb for Ubuntu that isn't allowing for anything else. You should at least have a 3gb for root. I don't know how much you want to use but you should do at least 10gb, Either make one 10gb partition for root and let root store home or make a 5gb for root and a 5gb for home.
2 is cutting it way too close. If you wanted to keep it minimal use 1 partition of 5gb. (Besides these partitions you still need a swap partition of 512mb or so)
Like I said I trust grub and don't know acronis so I can't comment on anything that it might be causing.

---

### Post by MojoWorkin on 2006-06-04
Thanks again for replying so soon. 
But, I didn't wait, as my intincts told me also, that 2GB was way to small as well.
So, I just re-installed onto the 40GB drive I use for Ubuntu, and chose 50% for root:
(18.9GB) and I have a File System Volume I can't see space of, containing other Linux files, and the FAT32 (named) partition I also can't "see" into. This FAT32 is what I wanted for shared files between WinXP and Ubuntu. I am guessing, I need to "mount" it? including format?
I still haven't yet plugged in the WinXP drive, I am solo on 6.06 now.
b.t.w. I run 2GB RAM, so a small swap would be ok, but I still have 854MB.
Partition 1 is 18.9GB with 15.74GB free.
Part. 1 is Root? right? 
Partition 5 is 17.53GB but not enabled or formatted.
Part. 5 is where I add files to use?
Should I format FAT32 part. and mount it first? before adding WinXp back into system?
I'm dnld Automatix now, and will be here for a bit.

---

### Post by catlett on 2006-06-04
First run these two commands and then paste the results in a reply```
 sudo fdisk -l
``` ```
sudo gedit /etc/fstab
``` The first one is a listing of your partitions. The second one is the configuration file that deals with mounting partitions and drives on startup. This way we can see what partitions you have and which ones are mounted on startup.

---

### Post by MojoWorkin on 2006-06-04
I jumped the gun, and tried to format the FAT32 (named) part. as /home... woops...
I couldn't access anything for there, no Computer, no admin. tools, etc.
So, I reinstalled, formatted whole drive, and this is what I have now:
37.7GB Total size drive
35.7GB Root Volume  (31.47 free) (partition1)(dev/hdd1)
1.54GB Swap (dev/hdd5)
Guess I can place /home in /root?
Sorry, I was impatient, and jumped too soon, but I want to get this thing going and install some accessories to see what I like about it.
I can't enter the above commands, because it asks for password, I enter admin. password I created, and it says sorry...

---

### Post by catlett on 2006-06-04
First when you type sudo the password youi use is the pasword you log on with, your user password.
Second your configuration is fine. You can have 1 big partition and have home installed there. Home IS already installed there if you ran the install and you are in your setup.
Home on a seperate partition isn't necessary but it is advisable. It keeps your personal data seperate from the filesystem. This way if you upgrade or ned to reinstall for some reason home is dafe and doesn't get reformatted.
BTW The good news is your configuration is fine. Asd long as when you go to the top of the screen and hit on "Places" there is an option for "home" then you are fine. Home is installed on the same partition as root and this is OK.
Is there a fat32 partition that you made but can't see? If not that is alright too. Ubuntu can read your windows data (it just has issues with writind data to it, still a bit buggy) and windows can read/write your ubuntu data when you install the driver "ext2.fs". There is a link to it in my signature.
So you are fine. Use Automatix for dapper or follow the guide in my signature to get what you want installed.

---

### Post by MojoWorkin on 2006-06-04
Guess I can clarify one thing:
Yes I made a FAT32 Partition, and named it FAT32, but that is all used now, as /root + /home + /swap now.
Gonna rename it Tux, for easier explainations later on.
I'll create another partition on another drive as FAT32 for sharing files later.
Kewl, I'll leave my home in root, and start Automatix now.
I'll copy all the links in your sig, and start investigating them.
Thanks again, for the walk through...
(gone to grab rogaine bottle...)
:p

---

