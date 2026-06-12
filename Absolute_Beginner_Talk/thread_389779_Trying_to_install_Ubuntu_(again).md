---
title: "Trying to install Ubuntu (again)"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by iamnu on 2007-03-21
I have had no success installing Ubuntu, even though many of you have tried to help.  I have been doing some research, and maybe have the solution to the problem, but I wanted to run it by you first.

My cruddy little Dell Latitude d233st was originally run with the Windows 98 OS.  I don't know how much hard disk is available, nor even how much memory, but I think it may be 256mb.

I downloaded Ubuntu 6.06 from this site: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), and after inserting the CD in my laptop, I got the message " [17179711.7000007] hdc: drive not ready for command."

While I was _unable_ to get past this message on my laptop, I did use the same CD on my desktop, and it worked just fine (I did not "Install" it on my desktop, just ran it from the CD).  So I guess I have concluded from this, that I don't have enough memory or Hard Drive space on my laptop.  Would that be true?

So now I learn there is something called "Ubuntu Live CD".
Is this any different from what I downloaded?  If so, where do I get it?
Will this run without sufficient hard disk space?

Thanks for the help, and suggestions...

---

### Post by overdrank on 2007-03-21
> **iamnu said:**
> I have had no success installing Ubuntu, even though many of you have tried to help.  I have been doing some research, and maybe have the solution to the problem, but I wanted to run it by you first.

My cruddy little Dell Latitude d233st was originally run with the Windows 98 OS.  I don't know how much hard disk is available, nor even how much memory, but I think it may be 256mb.

I downloaded Ubuntu 6.06 from this site: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), and after inserting the CD in my laptop, I got the message " [17179711.7000007] hdc: drive not ready for command."

While I was _unable_ to get past this message on my laptop, I did use the same CD on my desktop, and it worked just fine (I did not "Install" it on my desktop, just ran it from the CD).  So I guess I have concluded from this, that I don't have enough memory or Hard Drive space on my laptop.  Would that be true?

So now I learn there is something called "Ubuntu Live CD".
Is this any different from what I downloaded?  If so, where do I get it?
Will this run without sufficient hard disk space?

Thanks for the help, and suggestions...

Hi and welcome, I search your laptop and the max memory you can have is 256mb and you might have a small hard drive but that should not stop the cd from running only the amount of ram. You might try xubuntu alternate cd
[http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/)
And be sure that you use the how to burn instructions.
Now the cd you have and ran in your desk top is a live cd, you can run the os without doing anything to your system and the same applies to your laptop. Hope you enjoy and good luck!

---

### Post by buuntuu! on 2007-03-21
as paul capps says, 256mb is enough ram to run the live cd (desktop cd- it's the same, don't be confused, people use both terms synonymously) which is what you have downloaded
but if you have trouble running from it you might try the alternate-install-cd, which helps in case the live-cd gives some trouble. it is essentially the same, just without the option off running the OS without installing and there is only a text-based installer, no nice graphical user interface during install...
get it here[http://releases.ubuntu.com/dapper/]("http://releases.ubuntu.com/dapper/")
if you definately want the gnome desktop, but if your lappie is old and low on resources follow paul capp's link to xubuntu.

but if you really want to get your system going i recommend a server-install to which you can add an even lighter window-manager, like openbox. 
follow this [thread]("http://www.ubuntuforums.org/showthread.php?t=103806") for a good howto

EDIT: oh, and check out [psychocat's]("http://www.psychocats.net/ubuntu/") great site for all that is concerned with installation etc. allways good to know what one is doing...
have fun

---

### Post by iamnu on 2007-03-21
Okay, thanks...

I will download a new CD and give it another try, then report back in a few days.

Thanks for the link to Psychocats Ubuntu page.  I have been needing this kind of detail.

---

### Post by iamnu on 2007-03-25
I have now used the site [http://releases.ubuntu.com/dapper/](http://releases.ubuntu.com/dapper/) and downloaded the PC (Intel x86) alternate install CD.
I then inserted the CD into my little laptop and powered up.
Unfortunately I forgot to write down the option I chose on the initial screen, but it was the first one in the list..."Install with text" (or something like that).

I then received the following messages:
1. Low Memory Mode
2. Set up swap space as soon as possible
3. The CD-ROM does not seem to contain a valid "Release" file.  You may try to repeat CD-ROM detection but, you may experience problems later in the installation.
4. An installation step failed.  The failing step is: Detect and mount CD-ROM.  <Continue>
5. Run Detect and mount CD-ROM (again).
6. Installing the base system
7. Hostname: <entered>
8. Username: <entered>
9. Password: <entered>
10. Erase entire disk: IDE1 master (hda) - 4.3 GB IBM-DKLA-2430 

After this, it essential went off "installing" on its own, then ejected the CD-ROM, and rebooted.

After reboot, it asked me for my username and password, gave me the Ubuntu disclaimer "Ubuntu comes with ABSOLUTELY NO WARRANTY..."  message and then came to rest at the following line:

myusername@myhostname: ~$

So what am I suppose to do now?
How do I get out of this "DOS" like environment and into a graphical one?
How do I "Set up swap space as soon as possible" as directed?

---

### Post by buuntuu! on 2007-03-25
as i have never installed with an alternate cd i cannot help much here...
point 3. is strange though... did you control the md5sum of the download and integrity of the burned cd? 
installing with alternate is text only, but you should have a window manager then... probably your install went wrong at some point
try ```
startx
```
if you HAVE a windowmanager installed it should open.
if not, put in your install cd again and perform the disc integrity check...
take a look at [this howto]("http://users.bigpond.net.au/hermanzone/p2.htm"), its about dual booting, but the installation with the alternate cd is explained well. if you can't find out what went wrong you could install following its directions

---

