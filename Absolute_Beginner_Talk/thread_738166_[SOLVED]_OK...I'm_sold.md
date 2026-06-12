---
title: "[SOLVED] OK...I'm sold"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by SaddleTramp on 2008-03-28
HP Pavilion a1700n
ASUS A8M2N-LA (HP NODUSM3-GL8E) Motherboard
AMD 3800+ (1.7GHz) 64 x2 dual core Processor
1GB Ram
Award Bios
Onboard nVida GeForce 6150LE Chipset (Video)
Onboard nVida nForce Network Controller
Onboard RealTek HD Audio (ALC888 Codec)
250GB Samsung SCSI HDD
Windows Vista SP1 RTM
HP Officejet 6310 AIO

Running Vista host with VirtualBox'd Guest Unbutu.

All specs can be seen here:  [http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=us&lang=en&dlc=en&product=3339286](http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=us&lang=en&dlc=en&product=3339286)

Impressed with Ubuntu 8.04beta (use to beta testing so thought I'd give it a shot, if it's gonna aggrevate me, it'll be in the beta :) ).

Had 2 minor(?) problems:

1.  Couldn't get the VBoxLinuxAdditions to install until (and this may help some others) I burned the GuestAdditions.iso to CD.  Mounted the physical CD, not the .iso image under Innotek folder, opened the CD that came up on Ubuntu Desktop, then started Terminal.  Changed to directory of the CD and ran VBoxLinuxAdditions.run from there.  Installed without a hitch.

2.  Updates would not download due to update manager not able to mkdir (make directory) /root under /home.  Started Terminal, changed to /home and mkdir /root myself.  Updates went fine after that (231 of'em).

So all in all, after a day and a half, I have a heckuva Virtual Ubuntu running in Vista.

Here's the catch.  The whole HDD is partitioned for Vista.  So I need to shrink the partition (hopefully without having to reinstall everything), then install Ubuntu 8.04 (hopefully there's a way I can migrate the VBox'd Ubuntu I already have installed and working).

Also, I really need to make sure the programs I'm running under Vista will run under Ubuntu (hopefully with Wine, Cedega, or something else).  Mainly my DVD and video editing programs.  I'm using DVD Rebuilder, DVDFab Decrypter (in a strictly legal sense as I only backup MY DVD library), ImgBurn, and some similar to these that are more specific as to what part of video/audio they edit.  Or maybe there's something already out there that will just run under Ubuntu that will do the same thing.

What do you folks think.  Is all this possible, and if not, maybe some advice on the easiest way to do this.

Thanks in advance for any info and wishing now I had went the Linux way years ago.

Thanks again
S'Tramp

---

### Post by piousp on 2008-03-28
I think is posibble to resize your vista's ntfs partition within vista itself.
About your burning apps, i would suggest you take a look at Nero Linux, and K3B (KDE app).
I'm not sure if its possible to "move" your already installed vbox ubuntu to a "real" machine. I'm leaning to think that is not posibble, but who knows!

Also, you can just install Wine in ubuntu, and try your apps under vbox. If you do run into some problems running the apps, i would suggest tackling winehq and read the terminal's output to see if the problem is related to some missing DLLs. Welcome aboard buddy!

---

### Post by wheredidrealitygo on 2008-03-28
it is definitely possible to resize your Vista partition from within Vista.

You need to run the command "mmc" (which stands for microsoft management console) from the search box in vista in the start menu,
then go to file, add/remove snap-in, and do (trying to remember) disk management.

then it should show you all your hard drives and you can just resize from there.

---

### Post by lswest on 2008-03-28
to resize in vista:
right-click my computer, choose "manage" and go to disk management.

Migrating from Virtualbox to your laptop:
not possible.  At least, it would be a hell of a lot of work, since virtualbox uses generic hardware (basically, it makes virtual hardware) which works in linux, but the drivers used for those are installed and enabled.  Guess what?  Those drivers won't work for your computer.  However, you can make a backup of your programs/documents, save the tar.gz to an external hdd, and then restore it in a fresh install.

---

### Post by SaddleTramp on 2008-03-28
Thanks Piousp...
 
I think there is in Vista myself, at same time wondering if anyone's done it without any problems. As for the editing, the editors I use let me get 'inside' the .ifo/.vob files themselves. For burning, Nero and the like would just be more money which is what I'm trying not to have to invest any more in. 
 
Thanks again

---

### Post by wolfen69 on 2008-03-28
you will be better served resizing your partition and re-installing. a fresh install is always best.  download another image from here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) it is the daily build of hardy. it will save you from having 400 updates after install.

---

### Post by SaddleTramp on 2008-03-28
Thanks Ya'll..
 
That pretty much takes care of resizing the partition.
Migrating would have been nice (and should have already realized myself it wouldn't work for reasons given by LSWest.  And since I'm still keeping Vista going for awhile, I'm sure I'll eventually get to something I can use for editing in Ubuntu or otherwise just use the Vista for that.
 
Thanks again folks.  That's a wrap then.  All questions answered.  Ya'll take care and I'll cya around...
 
S'Tramp

---

### Post by piousp on 2008-03-28
Your welcome!
I have no experience with the apps you use :( In anycase, as i was saying, you could just install wine under your vbox's ubuntu and try your apps there. If they run, your all set!

To install wine, you can use ubuntu's repos:

```

sudo apt-get install wine

```

Or [you can add wine's repo]("http://www.winehq.org/site/download-deb") and then install it.

---

### Post by SaddleTramp on 2008-03-28
Will do that for sure Wolfen...thanks much for the tip

---

### Post by SaddleTramp on 2008-03-28
Thanks again Piousp, will do that tonight. And prolly after go ahead and resize and reinstall.
 
Wow!! Ya'll are quick in here.  Looks like I'm making the right choice!!

---

### Post by SaddleTramp on 2008-03-28
Shoot...just thought of 1 more question (more out of curiosity) while I'm here...
 
Since I'll be repartitioning and installing, can I install Ubuntu 64 bit (Vista is 32 bit) ???  Thanks

---

### Post by Seisen on 2008-03-28
If you computer is 64-bit than yes you can but if its 32-bit than no. Also make sure to defrag you hard drive before you partition it otherwise you can run into problems afterwards.

---

### Post by piousp on 2008-03-28
Glad to be of help! :)

---

### Post by piousp on 2008-03-28
Also, personally i would install the 32bit.
About defrag: you wont have to worry about it in linux, as for windows.... well, lets just say we all know ;)

---

### Post by SaddleTramp on 2008-03-28
> **Seisen said:**
> If you computer is 64-bit than yes you can but if its 32-bit than no. Also make sure to defrag you hard driver before you partition it otherwise you can run into problems afterwards.
 
 
Thanks Seisen...
 
This just keeps gettin' better !! Have AMD Athlon 3800+ 64 x2 dual-core...shouln't have any problems then.
 
Thanks again all of you...
S'Tramp

---

### Post by SaddleTramp on 2008-03-28
> **piousp said:**
> Also, personally i would install the 32bit.
About defrag: you wont have to worry about it in linux, as for windows.... well, lets just say we all know ;)
 
Gonna try the 64 bit...if too many problems then I'll step back down to the 32 bit..
 
And defragging the Vista for sure :lolflag:
 
Thanks again !

---

### Post by piousp on 2008-03-28
I just read your sig:

> The 3 rules: 1. Research; 2. Read; 3. Repeat Rules 1 & 2...

Nice!

---

### Post by SaddleTramp on 2008-03-28
Thanks Piousp

---

### Post by dcstar on 2008-04-05
> **piousp said:**
> 
About defrag: you wont have to worry about it in linux, as for windows.... well, lets just say we all know ;)

The defrag is to prepare for NTFS partition resizing, it is a good policy to always do a native Windows defrag before resizing (with any tool).

---

### Post by SaddleTramp on 2008-04-05
Well I tried every way of resizing Vista I could find here in Ubuntu forum and a few other places...no joy.  Something to do with the OEM version has something set that won't allow me to.  Tired of buying something only to have some big shot corp trying to control me another way. Soooooooo...stripped Vista and said so long to the 'dark side' :lol: (MS) and now have Ubuntu Hardy running on 1 drive and Ubuntu Ultimate on the other dual booting like a champ. Thanks for all ya'lls help and add another 'convert' to the Linux side. 8-)

---

### Post by Helios1276 on 2008-04-05
tsk tsk hardy heron on the normal threads ;) lol

---

### Post by SaddleTramp on 2008-04-05
> **Helios1276 said:**
> tsk tsk hardy heron on the normal threads ;) lol
Wellllll...after all it was my 1st post before I got educated ;)

---

### Post by piousp on 2008-04-06
> **SaddleTramp said:**
> Well I tried every way of resizing Vista I could find here in Ubuntu forum and a few other places...no joy.  Something to do with the OEM version has something set that won't allow me to.  Tired of buying something only to have some big shot corp trying to control me another way. Soooooooo...stripped Vista and said so long to the 'dark side' :lol: (MS) and now have Ubuntu Hardy running on 1 drive and Ubuntu Ultimate on the other dual booting like a champ. Thanks for all ya'lls help and add another 'convert' to the Linux side. 8-)

Woah woah! Nice!

---

### Post by sailor2001 on 2008-04-06
vista only allows just so much partitioning (size), however a linux live disk will help squeeze  that smaller.  As far as burners, k3b and gnome baker (in synaptics) are both excellent ..and guess what?  it's ALL FREE

---

