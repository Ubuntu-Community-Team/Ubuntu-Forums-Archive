---
title: "Please Help: Cannot transfer files from Ubuntu to Windows"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by insyted on 2007-02-21
I have an computer with Ubuntu as the OS.
I have a another computer with Windows XP installed on it.

I took the hard drive out of my Windows XP computer. I connected it to my Ubuntu computer via IDE in order to transfer files from my Ubuntu computer into the hard drive with Windows XP on it.

In Ubuntu, I mounted the WinXP drive into the media folder, and opened it. Everything was fine. All the files were there.
I tried copying files from my Ubuntu computer into the WinXP hard drive.

I got an error:
"You do not have permission to write to this folder.

I have my C drive shared with full permissions on my WinXP hard drive. I also have my Administrator folder shared in the Documents and Settings folder.
I did not set the Documents and settings folder to share though.


I tried to copy the files directly to the C drive, and they did not go through because of the error.
I have no problem copying any file from that WinXP hard drive into my Ubuntu hard drive.

---

### Post by taurus on 2007-02-21
Is your XP an ntfs filesystem?  You can't write to ntfs filesystem unless you install ntfs-3g driver first.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by insyted on 2007-02-21
Thanks. I'll try it out.
Yes theWinXP  drive is NTFS.

---

### Post by insyted on 2007-02-21
Please tell me how I can install the ntfs-3g driver.
I don't understand any of the instructions on the other page.

Do I have to open up the terminal command prompt?
Do I have to download anything from online?
How do you download from online?
I don't know how to usemuch of  anything in Ubuntu.

---

### Post by insyted on 2007-02-21
It says on the 64bit instructions:
"For edgy, ntfs-3g is in universe, so you'll not need my repo"

I use 64, so what does this mean it is in universe? How do I access the universe?

---

### Post by Maestro23 on 2007-02-21
> **insyted said:**
> It says on the 64bit instructions:
"For edgy, ntfs-3g is in universe, so you'll not need my repo"

I use 64, so what does this mean it is in universe? How do I access the universe?

Enabling Extra Repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then you can install ntfs-3g via Synaptic(GUI) or apt-get/aptitude(command line).

---

### Post by bodhi.zazen on 2007-02-21
IMO the easiest way to install ntfs-3g is with ntfs-config

ntfs-config is a gui front end for ntfs-3g

[How to ntfs-config](ntfs-config : http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by insyted on 2007-02-21
I got up to here:
"Save your file and close either kwrite or gedit. Lastly, and most importantly, type this into the terminal
[sudo aptitude update ]"

Things are happening now within the terminal.
I guess  wait until it is finished.
What do I do after that?

---

### Post by bodhi.zazen on 2007-02-21
which tutorial are you following ?

---

### Post by insyted on 2007-02-21
I did this one only because I could understand the steps.

"Enabling Extra Repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then you can install ntfs-3g via Synaptic(GUI) or apt-get/aptitude(command line)."

I proceeded into the Synaptic, and saw ntfs-3g there. So I checked it to mark for installation. It installed, and I restarted.
I still cannot transfer the files.
Should I do anything else?
I checked back in Synaptic. Here is the screen:
[http://img339.imageshack.us/img339/6979/screenshotzj6.png](http://img339.imageshack.us/img339/6979/screenshotzj6.png)

---

### Post by insyted on 2007-02-21
I would tell my computer to boot into the WinXP drive. It's a Western Digital IDE. I took off the slave jumper. The Ubuntu is a Seagate SATA drive. I went into the bios, and set the Western Digital as the primary boot device. I don't know how to set my Seagate as a slave as it has no jumpers, so I just left it as is. When I tried to start up into the WinXP drive, the computer sent me to a screen about starting  Windows normally or in safe mode. No matter what option I chose, the computer never started up windows. It just restarted.
Either way I don't know if I can grab the files from Ubuntu, and send them into WinXP.

---

### Post by Maestro23 on 2007-02-21
Here is a link discussing "NTFS-config": [http://www.ubuntuforums.org/showthread.php?t=337970&highlight=ntfs-config](http://www.ubuntuforums.org/showthread.php?t=337970&highlight=ntfs-config)

---

### Post by insyted on 2007-02-21
So on a fresh install, the only things you'll have to do is :
- install ntfs-config.
- click on 2 button, wait for the device to be remounted, and that's all.

What does "so on a fresh install mean"?
There are no instructions for installing ntfs-config.

What about the ntfs-3g?
Shouldn't that be able to let me do everything I need?
Did I install it right?
Why isn't it working?

---

### Post by george29 on 2007-02-21
i understand what you are trying to do - but it seems like an awful lot of faffing around. 

if you just want to transfer some files why don't you use a USB flash drive?

---

### Post by insyted on 2007-02-21
It's over a hundred gigs. The fastest way is from the hard drive.
I would probably try to change the file system on my Ubuntu driv to NTFS, and then set it as a slave.
Then take the files by starting up in the WinXP hard drive.
I just don't know how to do any of that.


The only thing I can think of is to get Ubuntu to write the files to the other drive, but nothing seems to make sense. I do not even know if ntfs-3g is installed. What is ntfs-config? Isn't ntfs-3g supposed to do it?
There are no instructions for ntfs-config whatever that is, and the links are all bad.

---

### Post by igknighted on 2007-02-21
You need to remount the drive with the file type ntfs-3g instead of ntfs.  This should give your write access.

EDIT: You could have done the opposite, as WinXP can read Ubuntu's ext3 partitions perfectly.  In fact this would be the preffered way of doing it, as ntfs-3g is beta, and for transferring large amounts of data I would be uneasy.

EDIT2: You cannot change Ubuntu's partition to ntfs because linux does not support ntfs.

---

### Post by insyted on 2007-02-21
Thanks igknighted. Nobody mentioned that I have to mount it like that. Please tell me how to do it. Normally when I mount the drive I have to enter this code into the terminal:
sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Is there another code to do it as ntfs-3g? Do I just add the- 3g in?

---

### Post by igknighted on 2007-02-21
> **insyted said:**
> Thanks igknighted. Nobody mentioned that I have to mount it like that. Please tell me how to do it. Normally when I mount the drive I have to enter this code into the terminal:
sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Is there another code to do it as ntfs-3g? Do I just add the- 3g in?

Yup, just add -3g so it looks like:
```
sudo mount /dev/sdb1 /media/windows/ -t ntfs-3g -o nls=utf8,umask=0222
```

How much data do you plan on moving?  If its a really large amount (>15 GB) I would strongly recommend you try doing it from windows.  It is possible that using ntfs-3g you could corrupt the windows file system (not a real worry for small file transfers, but something enormous you should be aware).

---

### Post by insyted on 2007-02-21
Here is what I did from the beginning:

I opened up the terminal, and entered:
> sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

Then the text editor appeared.

I entered the following into the text editor:
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 


I saved and closed the text editor.

I then entered the following into the terminal:
> sudo aptitude update

Some things started running. I waited for it to complete.
I opened Synaptic, and searched for the ntfs-3g.
I marked it to install, and proceeded with the installation.

Then I restarted.

Then I mounted the slave drive using the following code:
> sudo mount /dev/sdb1 /media/windows/ -t ntfs-3g -o nls=utf8,umask=0222

It still does not allow me to put any files into my WinXP drive.

---

### Post by george29 on 2007-02-21
fair enough... i can see why you wouldn't want to use a flash drive... 

can't help you with the code for mounting ntfs drives with write support as i use FAT32 partitions so i can transfer data between XP and ubuntu.

hope you get it all sorted...

---

### Post by igknighted on 2007-02-21
Try adding this line to your fstab and restarting:
/dev/sdb1		/media/windows		ntfs-3g 	defaults	0 0

---

### Post by insyted on 2007-02-21
Is there a reason why Ubuntu is configured like this?
Would the same problems occur if Ubuntu was conncected to a Windows computer via ethernet?

---

### Post by insyted on 2007-02-21
> **igknighted said:**
> Try adding this line to your fstab and restarting:
/dev/sdb1		/media/windows		ntfs-3g 	defaults	0 0
What does this mean?
What is an fstab, and how do I add this line into it?
Please note, I am an "Absolute Beginner", and have no idea how to do anything in Linux save what I learned about the basic terminal commands including how to mount  slave drive onto it.

---

### Post by george29 on 2007-02-21
as far as i'm aware even if you were connecting via ethernet you'd still need ubuntu to be able to write to an NTFS partition.. unless you were going to share the files you want to move using SAMBA... I don't know the particulars of how to do that - but i'm sure there are others around who could enlighten you.

you could of course try installing drivers in windows that allow it to read linux partitions and then copy the data over that way...

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

edit - this depends on you using Ext2 or Ext3 filesystem on your ubuntu drive.

fstab - is a file that describe the mount points, partitions etc on the system.. [http://www.cae.wisc.edu/site/public/?title=linfstab](http://www.cae.wisc.edu/site/public/?title=linfstab)

george.

---

### Post by igknighted on 2007-02-21
> **insyted said:**
> What does this mean?
What is an fstab, and how do I add this line into it?
Please note, I am an "Absolute Beginner", and have no idea how to do anything in Linux save what I learned about the basic terminal commands including how to mount  slave drive onto it.

The fstab is a file that tells Ubuntu what filesystems are accessable and where and how to mount them.  This is done at boot so you dont have to manually mount them.  You can edit it by typing this into a terminal:
```
sudo gedit /etc/fstab
```
then just paste the line from above in to the bottom of the file, hit enter to add a blank line at the end, then save and restart.

---

### Post by igknighted on 2007-02-21
> **george29 said:**
> as far as i'm aware even if you were connecting via ethernet you'd still need ubuntu to be able to write to an NTFS partition.. unless you were going to share the files you want to move using SAMBA... I don't know the particulars of how to do that - but i'm sure there are others around who could enlighten you.

you could of course try installing drivers in windows that allow it to read linux partitions and then copy the data over that way...

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

edit - this depends on you using Ext2 or Ext3 filesystem on your ubuntu drive.

fstab - is a file that describe the mount points, partitions etc on the system.. [http://www.cae.wisc.edu/site/public/?title=linfstab](http://www.cae.wisc.edu/site/public/?title=linfstab)

george.

That driver works for both ext2 and 3, even though it has ext2 in the name.  The file systems are for all intents and purposes the same, just ext3 has a journal and ext2 does not.

---

### Post by Maestro23 on 2007-02-21
> **insyted said:**
> What does this mean?
What is an fstab, and how do I add this line into it?
Please note, I am an "Absolute Beginner", and have no idea how to do anything in Linux save what I learned about the basic terminal commands including how to mount  slave drive onto it.

Add the line he told you to: [COLOR="Red"]/etc/fstab[/COLOR]

Open a terminal, use an editor(vi, nano, gedit, kate, etc..) I use nano.

> sudo nano -B /etc/fstab

Add the line he told you to. Save and exit. Restart.

---

### Post by insyted on 2007-02-21
Thank you!
Finally Success. I saw the slave drive appear on my desktop, so I don't have to mount it everytime I restart my computer.

Everything works.

Ideally, Windows XP, and Ubutu could communicate with eachother on a network flawlessly. Meaning reading, writing, executing, etc. Without having to install extra drivers to do this. I hope this happens for the next upgrade as it seems tedious in terms of networking an Ubuntu computer to computers of other file systems.

Thanks again all!

---

### Post by igknighted on 2007-02-21
> **insyted said:**
> Thank you!
Finally Success. I saw the slave drive appear on my desktop, so I don't have to mount it everytime I restart my computer.

Everything works.

Ideally, Windows XP, and Ubutu could communicate with eachother on a network flawlessly. Meaning reading, writing, executing, etc. Without having to install extra drivers to do this. I hope this happens for the next upgrade as it seems tedious in terms of networking an Ubuntu computer to computers of other file systems.

Thanks again all!

Look into SAMBA if that is what you ultimately want.  It lets linux computers share in a windows workgroup, and is easy to set up.  There are lots of how-tos on the forums, try searching for "samba"

EDIT: The reason this is not default is because (I would guess here) many if not most Ubuntu users don't use windows at all and woudl really not want samba because it opens ports for no reason (and its an easy install from the repo's).  As for ntfs-3g, it is included in the 2.6.20 kernel I believe, so if that kernel makes fiesty it should be included.  it is late getting in because MS doesn't share specs for their file system so its been trial and error for linux to get it working with messing up the windows partition.  That said, it is finally becoming stable so it is going in the kernel.

---

### Post by insyted on 2007-02-21
That is good news.
If all I have to do is follow these steps to install the ntfs-3g driver, what is Samba for?

I have not gotten into networking in Unubtu yet, but I was wondering if there was a way to set the hard drive and all its contents open for full access from any computer on the p2p network. In Windows, this is not default. you have to right click on the C drive to open properties, and go to the share tab. Then set it to share. Then set it to allow other other users on network to change files.

I guess in order to get into my hard drive with Ubuntu, I would have to mount it first right? Then set it to share somehow? Not sure.

---

