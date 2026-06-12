---
title: "No CD-ROM drive detected when installing intrepid on iBook G4"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by sotoga on 2008-10-30
Hi

I just tried installing intrepid on my ibook G4, but I get this error:
"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy?
Yes No"


Could it be this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608) ?

---

### Post by crapple on 2008-10-30
I have an emac. Same problem. Anyone else having it. I don't know what to tell you other then download 8.04 and upgrade. Thats what I am doing

---

### Post by tiresia on 2008-10-30
I have the same issue, when I try to start from the Intrepid Installer. 
The upgrade from Hardy was performed without problems

---

### Post by darkmatter21 on 2008-11-02
I am also having this issue with a 500Mhz G3 iBook... anyone know of a workaround?

---

### Post by tiresia on 2008-11-02
> **darkmatter21 said:**
> I am also having this issue with a 500Mhz G3 iBook... anyone know of a workaround?
Here you can find a workaround
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by bazookaaa on 2008-11-03
> **tiresia said:**
> Here you can find a workaround
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

Is there any way to bypass this step if there actually is no optical drive? I'm trying to install Ubuntu from the hard drive (using [this guide]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html#boot-newworld")).

---

### Post by NewsAndHistory on 2009-01-13
I have the same question: Is there any way to bypass this step if there actually is no optical drive? I'm trying to install Ubuntu from the hard drive (using [this guide]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html#boot-newworld"))?

---

### Post by stream303 on 2009-01-13
Are you really just stuck at the detection of the cdrom with the xubuntu 8.10 installation?  That forum thread reference to using *modprobe ide-scsi* should work.

And the other thread you mentioned showing a G3 installation is what you'll be needing to do after getting it on the disk.  With the G3 iMac, it is mandatory to go back in and edit the /etc/X11/xorg.conf file manually.

Or, you could install 8.04 LTS which doesn't have the cd detection issue.

I'm afraid there isn't any "official" documentation, other than the wikis and threads here.

---

### Post by NewsAndHistory on 2009-01-14
I've burned and loaded the installation Xubuntu ISO for PPC (in this case, I'm using a iBook G3 600MHz - PowerPC), but it's not working because it **won't detect the CD-ROM drive, in which the installation disk currently occupies** on my computer. I can't bypass this huge stumbling block, so I need an alternative way to install Xubuntu.

How can I install & overwrite my out-dated OS X Panther (which was pre-installed on my iBook G3) and substitute it with XuBuntu 8.10 without using the the Xubuntu CD?

So far, After choosing Language, Country and Keyboard-Layout, the Installer tries to detect the CD-ROM, but you get following massage: 

[I]"No common CD-ROM drive was detected
You may need to load additional CD-ROM drivers from a floppy... Otherwise you willl be give the option to manually select CD-ROM modules. Load drivers from Floppy? - Yes - No"[/I]
I immediately answered 'No' to the previous question.

:confused: What should I do next? Is there an official Xubuntu guide for installing Xubuntu 8.10 on an old iBook G3? [This Ubuntu tutorial]("http://ubuntuforums.org/showthread.php?t=405934") isn't what I need. I need an official Xubuntu installation tutorial for noobs, who use iBook G3 users.

I don't see any tutorials that cover the steps I need to take, in the Apple Users section of this website. None of the instructions I got from similar forum-topics are not working for me:

[**PowerPC - Installing Intrepid (8.10) - No common CD-ROM drive was detected**]("http://ubuntuforums.org/showthread.php?t=964904")

---

### Post by stream303 on 2009-01-14
When that prompt about not recognizing the cd crops up, are you going into a different console via

ctrl-alt-f2

logging in, doing the modprobe ide-scsi thing, and then switching back to the first console via 

ctrl-alt-f1

?  Maybe this is where the problem lies.  Or, do you get nothing when you try ctrl-alt-f2 ?

---

### Post by edtech2020 on 2009-05-28
> **tiresia said:**
> Here you can find a workaround
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

I used this and it solved the CD not found problem. :)

Thanks!

---

