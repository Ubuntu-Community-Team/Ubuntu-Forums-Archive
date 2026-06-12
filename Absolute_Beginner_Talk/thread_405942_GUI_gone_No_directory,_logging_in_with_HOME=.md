---
title: "GUI gone: No directory, logging in with HOME=/"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-04-10
I have an older box that has been running 6.10 for a couple of months without any issues..up until now.  My GUI is now gone and I can't even login using the command line.  This is what I'm facing.

1. On power-up, the few lines of text at the beginning seems to be the usual. Quickly the Ubuntu logo and time bar appear, on a black background, and the time bar gradually "fills-up" as usual.

2. Rather than going to the next graphical stage, the screen stays black and in short order, the following text appears (MYCOMPUTER is this box's name):
[B]Starting up ...

Ubuntu 6.10 MYCOMPUTER tty1

MYCOMPUTER login:[/B]

3. I try logging in using my primary account, other accounts, and have even tried using "root", but in every situation I get the following:

**Last Login: Tue Apr 10 10:51:43 2007 on tty1 ** (note: this date/time does change)
[B]Linux MYCOMPUTER 2.6.17-11-generic #2 SMP Thur Feb 1 19:52:28 UTC 2007 i686

...standard UBUNTU legal stuff is here...

No directory, logging in with HOME=/
Cannot execute /bin/bash: Permission Denied[/B]

4. When I try to enter commands at the login prompt, I enter the command, then my password is asked for, I enter it, but I get the **Incorrect Login:** prompt. (To be expected.) Using "sudo" has no impact. The only action that seems to work is when I hit Ctrl-Alt-Del...then a system notice from root@MYCOMPUTER is displayed (confirming the upcoming shutdown.

**What was I doing at the time all hell broke lose?**
I was getting set to leave for a few days break.  Immediately before I was going to shutdown for the weekend, I was trying to tweak newly installed FIRESTARTER. Initially after setting up FS, I could access the internet through my LAN, see other boxes (although other window boxes couldn't see this box. [NOTE:The LAN was fine before I installed FS.] Then, this box couldn't see the LAN unless FIRESTARTER was turned off. This could have been because of how I changed my settings.

Now, I had enough mucking about with FIRESTARTER for the day. I believe the next thing I was trying to do was click on the shutdown option from the shutdown option box. However, it seemed that this box restarted without me clicking on anything (no, my mouse was not hanging over any option for more than a second).  The computer rebooted to what I see now.

I have searched the forum but have not found a similar situation.  Does anyone have a suggestion?

Thanks.

---

### Post by solar george on 2007-04-10
Can you boot up in recovery mode from the grub menu.

---

### Post by Ian-on-the-Trent on 2007-04-10
I guess I am a newbie!  LOL, didn't know I could do that.  But I have now tried.

I had a choice and selected recovery mode.  Text scrolled and stopped at root@MYCOMPUTER:~#.

Interestingly, the command line font changed right at the end of the text scrolling by.

I can see the directories when I type **ls -l** at the prompt.

---

### Post by solar george on 2007-04-10
OK, what partition layout have you got?
Do you have a separate partition for /home?
If so what do you get if you type
```
mount
```

---

### Post by Ian-on-the-Trent on 2007-04-10
Yes, there is  /home partition.

when I type "mount"...Yes, quite a bit of text is displayed. Are you looking for something in particular?

---

### Post by solar george on 2007-04-10
Does mount show any mention of /home?

---

### Post by Ian-on-the-Trent on 2007-04-10
No.  After I enter "mount", that word is not mentioned in the 10 lines that follow.

---

### Post by Ian-on-the-Trent on 2007-04-10
Continuing...

I did consider reinstalling GRUB (found at [http://ubuntuforums.org/archive/index.php/t-24113.html)](http://ubuntuforums.org/archive/index.php/t-24113.html)). However, I really was uncomfortable using the recommendations since I wasn't sure if this was THE solution to my issue.

Is it possible that I could have a HDD issues that has effected GRUB?  If anyone has any other ideas/suggestions/recommendations I'd certainly consider them.

---

### Post by solar george on 2007-04-10
Reinstalling grub wouldn't fix it.


try typing,

```
mount /dev/*home* /home
```

replace /dev/*home* with the partition that you put home on.

---

### Post by Ian-on-the-Trent on 2007-04-10
Thanks for your patience SG.

I'm concerned that I may risk losing files....should I be?

I'm not sure what you mean by replacing the partition.

---

### Post by solar george on 2007-04-10
> I'm concerned that I may risk losing files....should I be?

If there has been any file loss, then mounting the partition won't affect it further. You are simply doing what normal boot up does albeit manually.


Now would be a good time for a bit of advice that always makes sense after the worst has happened, ALLWAYS keep an up-to-date backup of any important files.

(It made sense to me only after I lost a lot of work after messing around, just too much, with my computer)

---

### Post by Ian-on-the-Trent on 2007-04-10
I'm not exactly sure what you mean by new partition.

Btw, regarding your...
> **solar george said:**
> Now would be a good time for a bit of advice that always makes sense after the worst has happened, ALLWAYS keep an up-to-date backup of any important files.



Is there an easy way to automate the backing up of files in ubuntu/linux?

---

### Post by Ian-on-the-Trent on 2007-04-10
> **solar george said:**
> try typing,

```
mount /dev/*home* /home
```

replace /dev/*home* with the partition that you put home on.


I tried your suggestion and got the following:

**mount: special device /dev/home does not exist**

Seeing that I seem to have some commands, would it be worthwhile to create an additional folder and copy my home files to it..as a backup?  Or am I confusing the matter?

---

### Post by solar george on 2007-04-10
When I said /dev/home I meant for you to replace it with the name of the device that actually has the /home on it. For me that is /dev/hda4.

> Seeing that I seem to have some commands, would it be worthwhile to create an additional folder and copy my home files to it..as a backup? Or am I confusing the matter?

As far as I can tell your /home is not accessible at the moment, however try,
```
ls /home/
```
If it comes up blank your home files are not accessible. Post the result and we can try to work from there.


As for backing up automatically you could use cron, (not very user friendly). I usually backup manually using rsync to another machine. It would  probably be best to do a search of the forums to  find out how to do an automatic backup.

---

### Post by Ian-on-the-Trent on 2007-04-10
I can access home and I can see the sub directories of the accounts I created. In fact, a was able to access sub directories of sub directories and the individual files.  The /home directory and its contents are still accessible.



I'm still a little uncertain of the syntax you use.  There is a /dev/ directory but I couldn't tell if there was a subdirectory /dev/home/. 

hda : the first hdd.  The 4 refers to the 4th partition on the first drive?


[QUOTE=solar george;2432966]When I said /dev/home I meant for you to replace it with the name of the device that actually has the /home on it. For me that is /dev/hda4.


As far as I can tell your /home is not accessible at the moment, however try,
```
ls /home/
```
If it comes up blank your home files are not accessible. Post the result and we can try to work from there.

when I type "ls -l /home/
the result is total 16
then four lines of home directories and the read/write privileges

---

### Post by solar george on 2007-04-11
OK to clear a few things up, /dev/home does not exist, it is shorthand for /dev/whateverpartitionhas homeonit, that is if you had a seperate partition for /home and it was the fourth partition on the first hard drive when I write /dev/home I mean /dev/hda4 and you should replace it with that in any commands.

In your case you don't appear to have a separate partition for /home there has been confusion somewhere.

Now try typing
```
su *username*
ls /home/*username*
```

In this case replace *username* with your username in the commands.


In these forums, when something is written in italics you need to change it to suite your computer so *username* in commands is replaces with your usual username. Hope that maked some sense.

---

### Post by Ian-on-the-Trent on 2007-04-11
Good morning.  Thanks for continuing your help.

I thought I had created a separate partition for /home/ when I installed Ubuntu but it is possible that I didn't. 
This said, when I type 
***ls - l*** 

I get a listing of all the main directories:
[COLOR="Blue"] lib, lost & found, media, mount, root, etc. [/COLOR]

However, /home/ does not appear in this list.  I can only get to /home/ by entering: 
***cd /home/***.  

Then I get the prompt:
***root@MYCOMPUTER:/home# ***

When I enter 
***ls -l***
the subdirectories for*** home ***are listed.

Is it reasonable to assume then that /home/ is in fact on a separate partition?


[COLOR="Purple"]In your case you don't appear to have a separate partition for /home there has been confusion somewhere.

Now try typing
```
su *username*
ls /home/*username*
```

In this case replace *username* with your username in the commands.[/COLOR]


I enter:  
***su ian***

The result:
***Cannot execute /bin/bash/: Permission Denied.***

I enter: 
***ls /home/ian***
The result:
***[COLOR="Blue"]Desktop Documents[/COLOR] [COLOR="MediumTurquoise"]Examples[/COLOR] [COLOR="Blue"]Personal To Be Sorted.[/COLOR]***

Incidently, right next to the box I'm having issues with, I have another running 5.1 Breezy.  This is my pseudo server (command line only). At no time do I ever see*** root*** in the syntax. When I'm prompted to login the computer name and Ubuntu version is listed:
[I][B]Ubuntu 5.1 "Breezy Badger" server1 tty1
server1 login:[/B][/I]

After loging in:
***ian@server1:~#***

[COLOR="Purple"]In these forums, when something is written in italics you need to change it to suite your computer so *username* in commands is replaces with your usual username. Hope that maked some sense.[/QUOTE][/COLOR]

*I apologize for seeming like a lunk, but for whatever mental block I have--maybe it's too many years on Windows (3.1 and onward)--I have a heck of a time understanding the logic of linux partitions, mounting, and differentiating directories from partitions.  I haven't yet grasped how one might defrag a drive...or is it a partition?  But that is for another day.*:confused:

---

### Post by solar george on 2007-04-11
> I get a listing of all the main directories:
lib, lost & found, media, mount, root, etc.

However, /home/ does not appear in this list. I can only get to /home/ by entering:
cd /home/. 

Well I have never seen anything like that before, it looks like you have got all of your file permisions mucked up. 

If you can get hold of a live cd (knoppix is best) try running that and use it to copy your files to a safe loction, after that I would recomend a reinstall of ubuntu, putting /home on a separate partition this time.

> 
Incidently, right next to the box I'm having issues with, I have another running 5.1 Breezy. This is my pseudo server (command line only). At no time do I ever see root in the syntax. When I'm prompted to login the computer name and Ubuntu version is listed:

On linux root is the superuser, it can do anything to your system, for that reason ubuntu keeps root shielded from normal users and scrambles the password to prevent acess, when you type sudo *command*, you are telling the computer to run that command as the superuser.

> time understanding the logic of linux partitions, mounting, and differentiating directories from partitions
There may be a guide in the wiki.

> I haven't yet grasped how one might defrag a drive...or is it a partition?
With the linux file systems you don't need to

---

### Post by Ian-on-the-Trent on 2007-04-11
Is there a way to find out what partitions exist from the CLI?

---

### Post by scrooge_74 on 2007-04-11
Did you ran out of space on the disk or the /home partition? type df on a command line and see if /home is full or something

also typing dmsg will give you some detail and may point you into the reason for your troubles

---

### Post by solar george on 2007-04-11
> Is there a way to find out what partitions exist from the CLI?

You can use cfdisk to view and edit the partitions, it is probably not install on your system however. (If you can get hold of the knoppix live cd it will have it installed) 

```
ls /dev/hd*
```
Will give you an idea of the number of partitons, not to be trusted on all distros, some have /dev/ entries for non-existant partitions.

---

### Post by jpkotta on 2007-04-11
I have the same problem.  This is what I was doing:

I was trying to install the dynamic dns client from no-ip.org.  I have already done this a long time ago on my desktop and I was installing it on my laptop.  I had built it and was doing a sudo checkinstall.  Now, this particular installer has a script that asks you which network interfaces to use, and I noticed that my eth0 was not listed (because it was not up), but that is the one I will be using primarily.  So I "ctrl-c"ed the command and then things went awry.  Suddenly I couldn't execute commands in the terminal, but I could still do things with the GUI (I run FVWM).  All of the terminals stopped working, and I could not start new ones, but window manager commands (close window, quit wm) worked.  I rebooted and X didn't start.  I have a root password, so I logged in with that, but could not su to my user(s).  If I try to log in from the console, it appears to log in OK, but fails with the error "can't cd to /home/jpkotta".  If I try to su after logging in as root, it simply says "No shell".  I'm baffled.

Further info:  I can't get the network up (wired or wireless).  I can't use sudo (permission denied, as root).  My partitions are mounted and not full.  I will post again after more investigations.  The hardware is fine because I'm typing this on the laptop with a live CD.

---

### Post by rajeev1204 on 2007-04-11
> **Ian-on-the-Trent said:**
> Is there a way to find out what partitions exist from the CLI?

 type this  sudo fdisk -l /dev/sda    (for sata drive else replace with hda )

(thats a small L btw after fdisk)
will list all your partitions

It seems like you have been able to login as urself  ian@ian,,,,,, ~$

If u say u can access home then it exists . 

type mount /dev/sda(n)  where n is for number . U will get this from the above command.

So if u have home on dev/sda5 then type mount /dev/sda7. If its already mounted it will tell u . so try the other linux partition . ie eg /dev/sda6 or something


this will show the mount points for the partitions .


good luck 



regards
rajeev

---

### Post by brentoboy on 2007-04-11
> **Ian-on-the-Trent said:**
> 
I enter:  
***su ian***

The result:
***Cannot execute /bin/bash/: Permission Denied.***

I enter: 
***ls /home/ian***
The result:
***[COLOR="Blue"]Desktop Documents[/COLOR] [COLOR="MediumTurquoise"]Examples[/COLOR] [COLOR="Blue"]Personal To Be Sorted.[/COLOR]***



You have permission issues.
When you boot into recovery mode, you are root *not ian* which is why it says "root....#"

The first thing I would do is grant root a real password so you can login as root without going to recovery mode.  You do that with the passwd command.

But, that is not going to fix the real issue here.  From what it sounds like you dont have full permissions to your own home folder, and you dont have excecute permissions on /bin/bash.  And, I'm guessing you have significant permissions issues all over the place.

What I would recommend is doing a mass "permission downgrade" and open your system up so that anything and everything is accessible to your normal user.  Once you can log in, backup your /home folder, and probably your /etc folder to CD or a network drive or something.

Then, Reinstall so that you have the right permissions on everything (so things work without being a security risk).

if you are game with what I am talking about, give ownership of all files to ian:

(no need to sudo, you are root)
chown --no-preserve-root --recursive ian:ian / 

and, just to make sure you have permission to execute /bin/bash

chmod ugoa+x /bin/bash

while you are at it, make sure the whole bin directory has execute permissions...

chmod ugoa+x /bin/*

(I've never tried to do that, so I dont know if that works -- then again, I've never done any of this, you have an oddball situation.) 

now, cross your fingers and try to boot "normally"

---

### Post by Ian-on-the-Trent on 2007-04-12
*[COLOR="Teal"](My apologies.  I hadn't refreshed this page and I missed the recent posts.  Below is what I have done in the meantime. I can easily reconnect the original HDD and proceed from there if necessary.)[/COLOR]*

After spending hours trying to get my system back up and running, unsuccessfully that is, I'm wondering if it might be better to somehow save my data stored in the /home/ directories then reinstall Ubuntu. Either that or somehow copy these files to new partition. I'd have to create this partition though.

Just to figure out how to do this, I disconnected the HDD, attached another old one, and installed Ubuntu (6.10).  During the installation I created 3 partitions: hda1, hda2 (swap), and hda3 (/home). This isn't exactly like my original installation, I didn't have /home on a separate partition on my working HDD.

Using Gparted on a Live CD, I attempted to reduce the size of hda1 and then transfer the space to hda3. This is what I've accomplished so far:
[LIST]
[*]reduced the size of hda1.
[*]added this available space to hda2 (swap).
[*]reduced the size of hda2.
[*]created a new partition (hda4) and added all the available disk space.
[/LIST]

What I can't do is transfer any space to hda3, the location of /home.  Am I totally messed up?  Does anyone have a better solution? (Such as reconnecting the main HDD as ab additional drive and mucking about with the 2 hard drives.)

---

### Post by Ian-on-the-Trent on 2007-04-12
I've taken a step back and reconnected the HDD in question. I am following the suggestions by brentoboy.

I successfully created a password for root.  I was able to login (CLI) without being in the recovery mode.

chown --no-preserve-root --recursive ian:ian /
(many, many denied messages appeared. However, when I checked the ownership of the directories (***ls -l***) all were owned by the su (***ian***)

chmod ugoa+x /bin/bash
(no apparent issues)

chmod ugoa+x /bin/*
(no apparent issues)

When I rebooted, I could login as root or the su.  But this was at the CLI.  *My GUI is still missing though*.

---

### Post by solar george on 2007-04-12
> When I rebooted, I could login as root or the su. But this was at the CLI. My GUI is still missing though.

when you say su I assume that you mean your usual usernam (su is the same as root).

Try running the command
```
startx
```

---

### Post by Ian-on-the-Trent on 2007-04-12
I have several accounts on this box.

[LIST]
[*]I created a password and can now log in as ***root***.
[*]My primary Ubuntu account is*** ian***.
[/LIST]

I typed in ***x*** at the CLI and a simple screen appeared with an X-type cursor for the mouse.  I did not have any options though.  I had to manually turn the box off to reboot; Ctrl-Alt-Del did not work.

After logging in, entering ***startx*** didn't do a thing.

---

### Post by brentoboy on 2007-04-12
login as root and run this, and tell me what it says:

/etc/init.d/gdm restart

---

### Post by Ian-on-the-Trent on 2007-04-12
The result from /etc/init.d/gdm restart after a fresh reboot and login as ***root***:

* Stopping GNOME Display Manager...     [ok]
* Starting GNOME Display Manager...      [[COLOR="Red"]fail[/COLOR]]

Of course, I'm still at the CLI

---

### Post by brentoboy on 2007-04-12
here is a conceptual overview of my new plan:

Turn the PC off and put in the second drive (have both drives connected)

Boot to a live CD

Format the second drive (the one that doesn't have important data)

Manually Mount both drives in the liveCD file system

Copy the entire home folder from the old drive over to the "root" folder of the new drive

Blast the permissions and ownership of the home folders to match the users they should belong to

unmount everything

install via the livecd

during installation, mount the second drive at /home

whammo, life is good.

---------
does that sound reasonable?
Which areas do you want explained, and to how much detail?

---

### Post by Ian-on-the-Trent on 2007-04-12
I'm not sure how to manually mount the drives.

I did reinstall Ubuntu on the old HDD.  Even though the original HDD was physically connected to the PC (Secondary Master) during the reinstall of Ubuntu, it wasn't mounted.

Another idea.  The old HDD is a 4GB unit, the original a 40GB.  Assuming I can backup the /home/ files, couldn't I somehow use the 4gb drive for programs and the 40gb drive for data? (Is email stored on the /home/ partition in Ubuntu?)

---

### Post by brentoboy on 2007-04-12
yeah, email would be on the home partition

do you have a network drive somewhere that you could use as a backup if we could get this thing booted up happily on a live CD?

Depending on what you have on there, you could very easily have more than 4GB in /home (and you might not)

But, if its only 4gb, there is no reason to make it your permenant home folder.

I can get you through manually mounting things no problem (but lets get a good gameplan first)

from within nautilus, you can right click a folder and pull up properties and find out how much space it is occupying.

so lets do this, first lets figure out if 4gb is enough for temporary storage (if its close, maybe we can dump some stuff that doesn't matter.

boot to livecd

lets find out the device names of your partitions

open the nautilus file browser and go into /dev and look for the stuff named hd*

what all is there?

---

### Post by brentoboy on 2007-04-12
in interest of time, here is the stuff you want for mounting

once you know your device names (probably /dev/hda1 and /dev/hdb1)

open a terminal window
and create a couple of folders to mount them in

```

sudo mkdir /mnt/hda1
sudo mkdir /mnt/hdb1
```

then, mount the partitions:

```

sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hdb1 /mnt/hdb1
```

now, open nautilus as root so you can do some heavy lifting...

```

sudo nautilus
```

you should be able to get into /mnt and see your data on both drives.
determine which is which, and lets go from there.

---

### Post by Ian-on-the-Trent on 2007-04-12
Thanks,

Yes, I do have two network drive with space.  An XP box and a linux box (running in a "server" CLI mode).  Both have enough space to store the 24GB of data.  I'm just getting Samba to run.  The box with problems is currently running in GUI...the reinstall on the smaller hard drive.

Just gotta figure out how to mount drives (I have your instructions.)

---

### Post by Ian-on-the-Trent on 2007-04-12
> 
do you have a network drive somewhere that you could use as a backup if we could get this thing booted up happily on a live CD? 

Must I use the live cd?

> Depending on what you have on there, you could very easily have more than 4GB in /home (and you might not)
Yes, I need much more than 4GB

> I can get you through manually mounting things no problem (but lets get a good gameplan first)

from within nautilus, you can right click a folder and pull up properties and find out how much space it is occupying.
I can't do this, the larger drive is not mounted.  I will try what you suggest in your following post.


> **brentoboy said:**
> boot to livecd

lets find out the device names of your partitions

open the nautilus file browser and go into /dev and look for the stuff named hd*

what all is there?

Disk /dev/hda: 4324 MB, 4324368384 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         499     4008186   83  Linux
/dev/hda2             500         525      208845    5  Extended
/dev/hda5             500         525      208813+  82  Linux swap / Solaris

Disk /dev/hdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4795    38515806   83  Linux
/dev/hdc2            4796        4982     1502077+   5  Extended
/dev/hdc5            4796        4982     1502046   82  Linux swap / Solaris+9

BTW, the disks are listed under /dev/disk/by-id or by-path or by-uuid

---

### Post by Ian-on-the-Trent on 2007-04-12
> 
sudo mkdir /mnt/hdc1

Done and reflecting my system.

> 
then, mount the partitions:

sudo mount /dev/hdc1 /mnt/hdc1

This was done.

> 
sudo nautilus
you should be able to get into /mnt and see your data on both drives.
determine which is which, and lets go from there.
Yes, I can see the original ***/home/*** directory under ***/mnt/hdc1***.

---

### Post by Ian-on-the-Trent on 2007-04-12
FINE TUNING

When I rebooted, GRUB now gives me many different boot options including the installation that still resides on the original HDD. The only thing is, the mouse doesn't work for that boot option.  Strange indeed. (It does work for the new installation.)

[LIST]
[*]I assume that in order to clean up the boot options, GRUB needs to be edited.  How is this done? How do I remove the boot sector (at least make it unusable) of the original, larger HDD (hdc1).


[*]The original hard drive (now hdc) also contains hdc2 and hdc5. These are the logical partitions created for the initial installation's SWAP.  How do I get rid of them/add them to hdc1?


[*]Is there a way I can redirect the existing but data-empty /home/<username> on hda1 to the former home directories on hdc1?
[/LIST]

I cannot say why I lost my GUI in the first place.  The one lesson I learned though...ALWAYS ALWAYS ALWAYS put your /home/ directories on its own partition.  This has so far been a freakin' nightmare.

---

### Post by brentoboy on 2007-04-12
I think at this point, you need to get a network share going, and start copying things you like.

No matter what you do at this point, I dont  think you will get a "normal" system, back without a clean format of this box.

you are, what some people call "hosed" -- other people call it swiss cheezed.  You are unsalvagable.  Back up all the stuff in your home folder,  and make sure you take care to show hidden files (so you see all the folders that hold email and stuff.

once you have everything on the "safe" network drive, reboot into an install cd and format everything.  Its like a religious experience.  Out with the old, and in with a new way of life -- leave it all behind.  Clean install.

If you are going to leave that 4GB drive in there, I would split it into two partitions.  One of them I would make 1 GB and mount it at /boot and format it ext2 (not ext3).  The other 3 gb I would use as swap space (so that your swap space doesn't reside on the drive that you do your work on).

4GB is just barely not big enough to be "everything but /home" so that's what I'd do with it.

I guess, post again if you have thoughts or questions about all that.

good luck, I hope it all gets backed up nicely, and then restored again after its all said and done.

---

### Post by Ian-on-the-Trent on 2007-04-13
> ...start copying things you like.
Can't seem to automount the 2nd drive (hdc1).  As well, I can't seem to figure out how to set up a SAMBA share for this drive.

> ...clean format of this box.
Arrrrggg...I figured it would come to this.

> ...You are unsalvagable.  
My wife sometimes thinks this as well.

> ...Its like a religious experience.  Out with the old, and in with a new way of life
Better not go there, I'm opinionated (I read a couple of your essays...well done)

> ...If you are going to leave that 4GB drive in there, I would split it into two partitions.  One of them I would make 1 GB and mount it at /boot and format it ext2 (not ext3).  The other 3 gb I would use as swap space (so that your swap space doesn't reside on the drive that you do your work on).
This seems counterintuitive to me.  Would it not make more sense to have a 3gb+ partition for everything but SWAP and HOME.  Set a 1GB partition for SWAP...I have 578MB of RAM and it won't be increasing it.

AND...why ext2?

>    4GB is just barely not big enough to be "everything but /home" so that's what I'd do with it.
I use this box for basic office type stuff: e-mail, word-processing, etc., and learning LINUX/software.  The 4gb should be fine for programs and swap.  The 40GB will be more than adequate for home files.  I hope :)

---

### Post by brentoboy on 2007-04-13
> **Ian-on-the-Trent said:**
> Can't seem to automount the 2nd drive (hdc1).  As well, I can't seem to figure out how to set up a SAMBA share for this drive.

Mount it manually like you did for the liveCD.  Create a folder for it at /mnt/hdc1 and then sudo mount /dev/hdc1 /mnt/hdc1 

> This seems counterintuitive to me.  Would it not make more sense to have a 3gb+ partition for everything but SWAP and HOME.  Set a 1GB partition for SWAP...I have 578MB of RAM and it won't be increasing it.


3GB is enough, but it leaves no room at all for expansion.  It would be easy to fill up 3gb+ by making the PC capable of booting to either Gnome or KDE.  Its not that it cant work -- obviously you got an entire functional system on the 4gb drive, its just that the root partition holds everything from all those "other" folders, and some of them expand when needed.  And you really don't want to have your root partition become uncomfortably full, so starting off with a tight fit at first could make it uncomfortable later.   It would be like buying a new warddrobe for your wife when she gets pregnant, and then watching her grow out of it because no one figured she'd get "that" big.  The worst part is that she doesn't get "that" big she just gets a little bigger than was planned for.

> 
AND...why ext2?

The primary difference between ext3 and ext2 is journaling -- a process that helps you avoid loosing data in scenarios where you update files on a somewhat continual basis.   Journaling adds a layer of complication, which is worth the effort if you have changing files, but ext2 (non-journaling) is more efficient and more stable -- so long as files are more or less write once, and read often.   The boot folder really just has your kernel, and you don't exactly update it often, so ext3 is unnecessary overkill.

> 
I use this box for basic office type stuff: e-mail, word-processing, etc., and learning LINUX/software.  The 4gb should be fine for programs and swap.  The 40GB will be more than adequate for home files.  I hope :)
Maybe what you want is to make a 10GB partition on your 40GB drive and use that for the root filesystem.  and then use the 30 gb for /home

Your filesystem would look like this:

/dev/hda1 -- 2GB -- mounted at /boot   (this is way overkill on the size by the way)
/dev/hda2 -- 2GB -- swap space  (also way overkill)
/dev/hdc1 -- 10GB -- mounted at /  (this is plenty of room -- not "way" overkill, but certainly plenty)
/dev/hdc2 -- 30GB  -- mounted at /home (this is plenty -- unless you rip dvds and such)

I think that's how I would do it.

As far as samba shares, share a folder from your windows box, and connect to it from your ubuntu box (using the samba client instead of making ubuntu a samba server).  Then, use the sudo nautilus trick to make sure you can copy anything you want without restrictions, and start moving things that way.

---

### Post by Ian-on-the-Trent on 2007-04-13
Thanks for all your help.

Right now, I'm backing up my data to a XP box and then burning DVD backups.  I was still having major headaches with the box in question, so I yanked out the larger HDD and mounted it to my "server".  The server's permission are quite open but at least I didn't have to mess about with it to much. I'm transferring 14GB of stuff as I type. After this is all done, I'll reinstall Ubuntu more or less along the lines of what you suggested.  

In the meantime, I'm rethinking my entire file system.  We have at least 4 computers hooked up to my LAN at anyone time.  One box is more or less my sons' gaming PC. The one I've been messing about with is my usual office computer.  Another is in the kitchen for homework and surfing, I have a server, and then I have various test PCs.  Some things are shared (multimedia), homework assignments need to be centralized, and eventually I need to setup a VPN so I can connect to my LAN while I'm away.  The learning never ends.

When all this is done, I'll summarize and conclude this activity.  Again ***brentoboy***...thanks, you've been a huge help.

---

### Post by jpkotta on 2007-04-14
1 GB is way too much for /boot.  My /boot partitions are usually 50 MB.  The kernel is getting bigger, so 100 MB is a better size.  You just have to remember to remove the really old kernels.  One kernel takes up about 15 MB (in /boot).  Ubuntu's kernels are mostly modules, and all of the modules go into / anyway.  This is the scheme I use:

/boot: 50 to 100 MB
swap: RAM to 2*RAM
/: 10 to 15 GB
/home: everything else

I have more thoughly described my situation here: [http://ubuntuforums.org/showthread.php?p=2452901](http://ubuntuforums.org/showthread.php?p=2452901)

---

### Post by Ian-on-the-Trent on 2007-05-30
I ended up reinstalling 6.06LTS on this box.  I was able to backup and save my data and although it took a while to get everything back in order, I did get it back.

Who knows what was behind the original issue.  In retrospect, having a better file management set-up, along with a back-up procedure, would have saved me hours and hours of work.  I could have simply re-installed the OS should an hour or so of troubleshooting prove fruitless. Live and learn.

One positive in all of this...all the contributors to the Ubuntu forums demonstrated why this distro is such a hot item...timely support when needed.

Cheers all.
Ian.

---

### Post by Nekiruhs on 2007-05-30
I dunno if this has been suggested before but maybe
sudo  chown -hR USERNAMEHERE /home/USERNAMEHERE

---

