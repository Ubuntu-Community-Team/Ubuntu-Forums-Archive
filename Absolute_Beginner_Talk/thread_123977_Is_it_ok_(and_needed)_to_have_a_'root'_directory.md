---
title: "Is it ok (and needed) to have a 'root' directory?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by asinsh on 2006-01-31
I've read in quite a number of posts here that you should not try to set up kubuntu with a root superuser.

When I initially ran the kubuntu installation cd and set up partitions for kubuntu, I did it using the "manually edit partition table" option (since I wanted to set up a separate home directory as well as a FAT32 directory to share with XP and a swap directory).

The installation program at first wouldn't let me actually make the changes so I messed around with it and finally was able to get it going by specifying that the main partition where I wanted to put kubuntu (the one with a mount of /) was a 'root' (I think that was in the 'mount options' area but I'm not sure).

Anyway, that worked fine and kubuntu is up and running, but now that I am just beginning to experiment I notice that when I tried to update I got some kind of error message about not being a root user.  (Sorry, but I'm not home with my computer so I can't recall the exact message.)

Did I already mess up?  Should I reinstall at this point?

---

### Post by aysiu on 2006-01-31
Read the third link of my signature. It explains everything...

... as long as you didn't do an expert install.

---

### Post by Joeb on 2006-01-31
The root directory is not the same as the root user.  All linux installations have a root directory, from which the other directories fall under.  Having a root user on the other hand is dependent on the distribution (and can always be added if one really wanted to do so).

So, in short, you do not need to reinstall.  As for your error message, where you trying to update from the command line?  If so you need to use sudo at the beginning of the command line and then enter your password when prompted.  If updating from inside Gnome, then you should be prompted for your password in a dialog box.

---

### Post by mvaniersel on 2006-01-31
> 
the main partition where I wanted to put kubuntu (the one with a mount of /) was a 'root'

This is a confusing sentence... What do you mean exactly? The / directory is often called the root directory, as it is the root of the filesystem. The root user is an account with unlimited access to the system. The two concepts are unrelated.

You do know how to run programs as root with sudo, right?

---

### Post by asinsh on 2006-01-31
> **"aysiu"]...Read the third link of my signature. It explains everything...[/quote]
Thanks, that link was useful (and your others are too).

[quote="joeb"]...The root directory is not the same as the root user. All linux installations have a root directory, from which the other directories fall under....[/quote]
Right, I knew that part.  But I was concerned that when I was creating the partitions for the system I may have inadvertently created a root user...but having read a bit more it seems like that's not the case (I did not use 'expert' install)

[quote="joeb"]...As for your error message, where you trying to update from the command line? If so you need to use sudo at the beginning of the command line and then enter your password when prompted. If updating from inside Gnome, then you should be prompted for your password in a dialog box.[/quote]
None of the above  said:**
> [quote='asinshesq"]...the main partition where I wanted to put kubuntu (the one with a mount of /) was a 'root'... 
What do you mean exactly? The / directory is often called the root directory, as it is the root of the filesystem. The root user is an account with unlimited access to the system. The two concepts are unrelated.  You do know how to run programs as root with sudo, right?[/quote]
Right, I do know that the / directory (root directory) is different from the root user, but as I mentioned above I wan't too sure about what I might have done while partitioning the drive during installation and was worried I may have messed things up...it sounds like I didn't.  As for knowing how to run programs with sudo, the answers is 'no, not yet, but I have a bunch of links to how to articles and I should have figured that part out by the end of tonight ;)

---

### Post by mvaniersel on 2006-02-01
[quote=asinsh]
I may have inadvertently created a root user...
[/quote]

The root user is always created, only, the account is disabled so you can't log in as root. This prevents newbies from developing the habit to log in as root, which is very wrong indeed. But a root user has to be created, a linux system wouldn't run without one. Many system and configuration files are owned by root.

[quote=asinsh]
no, not yet, but I have a bunch of links to how to articles and I should have figured that part out by the end of tonight
[/quote]
That is the correct answer :D

---

