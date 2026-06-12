---
title: "Truecrypt freezes when transferring files"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-02-08
I really like Truecrypt's new interface on the 5.0 release so I thought I'd give it a shot. I successfully 
created a standard encrypted volume with the fat filesystem (have also tried reiserfs), but when I 
attempt to transfer files to the volume, it will freeze after a couple minutes. Sometimes it will last 
longer than 10 minutes and others less than 5. None of the individual files are more than 100mb. 
Either way, it isn't very stable at all.

What could be the problem?

---

### Post by randy78 on 2008-02-09
Did you have a previous edition of Truecrypt installed before you installed 5.0?

I uninstalled all instances of Truecrypt before installing the new version and it works like a charm.

Good luck, and if anything, give EasyCrypt a try...

It's another front-end for TrueCrypt and is fairly stable and very intuitive.

Just search the forums for EasyCrypt:guitar:

---

### Post by shanepardue on 2008-02-09
> **randy78 said:**
> Did you have a previous edition of Truecrypt installed before you installed 5.0?

I uninstalled all instances of Truecrypt before installing the new version and it works like a charm.

Good luck, and if anything, give EasyCrypt a try...

It's another front-end for TrueCrypt and is fairly stable and very intuitive.

Just search the forums for EasyCrypt:guitar:
This was the first install of truecrypt installed. Easycrypt is a frontend for truecrypt. 
Everything seems to be ok with truecrypt until I transfer files either with nautilus or cp in 
the shell. I don't believe it is a problem with the frontend.

Thanks for the reply.

---

### Post by leftorvo on 2008-02-10
this happens to me too, not only transfering but encoding or muxing things. it happens often and always the same programs are frozen - firefox, azureus, xfce desktop and menu button, but not the terminal. shutting it down with a command doesnt do anything, I have to manually restart the computer with the power button.

i had an install where i uninstalled 4.3a and installed 5.0 and it did it, but i just installed my os again and it is doing it again :(

---

### Post by shanepardue on 2008-02-11
Here's the thread I am following on Truecrypt's forums. 
[http://forums.truecrypt.org/viewtopic.php?p=39379#39379](http://forums.truecrypt.org/viewtopic.php?p=39379#39379)

Also, I noticed the problem is fixed in Ubuntu 8.04 so if worse 
comes to worst, we can rely on a fix in 3 months. :)

---

### Post by leftorvo on 2008-02-14
ivymike says;

> It seems as though Syncon is correct in suggesting that newer versions of the Linux kernel resolve this issue.

So hopefully just a kernel upgrade can fix this... hopefully :X

---

### Post by shanepardue on 2008-02-15
> **leftorvo said:**
> ivymike says;



So hopefully just a kernel upgrade can fix this... hopefully :X
The most recent kernel update pushed down from the repos didn't fix it. Maybe the next one?

---

### Post by squelsh on 2008-03-19
Same prob here: Only hard-reset helps after trying to copy files on a TC-Volume...
My Sys: Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2))

Is there a fix? I need to do a crypted backup...

---

### Post by shanepardue on 2008-03-25
> **squelsh said:**
> Same prob here: Only hard-reset helps after trying to copy files on a TC-Volume...
My Sys: Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2))

Is there a fix? I need to do a crypted backup...
[http://forums.truecrypt.org/viewtopic.php?p=40912#40912](http://forums.truecrypt.org/viewtopic.php?p=40912#40912)

---

### Post by chewearn on 2008-03-28
> **shanepardue said:**
> [http://forums.truecrypt.org/viewtopic.php?p=40912#40912](http://forums.truecrypt.org/viewtopic.php?p=40912#40912)

Rats.  Is pita to register.

---

### Post by wieman01 on 2008-03-28
It basically says that you need to upgrade your kernel. Hardy (8.04) works well with Truecrypt and this problem should not occur any longer. Just upgrade.

---

### Post by shanepardue on 2008-03-28
> **AstalaVista said:**
> Rats.  Is pita to register.
Sorry about that..here's your fix without compiling a new kernel.

Settings -> Preferences -> Mount Options -> Filesystem Mount Options: sync

I've heard it doesn't work with the recent truecrypt that came out just this last month, but it does work on 5.0a. Hope this helps!

---

### Post by wieman01 on 2008-03-28
> **shanepardue said:**
> Sorry about that..here's your fix without compiling a new kernel.

Settings -> Preferences -> Mount Options -> Filesystem Mount Options: sync

I've heard it doesn't work with the recent truecrypt that came out just this last month, but it does work on 5.0a. Hope this helps!
It has issues with the latest version, the thread in Truecrypt's forum confirms it. Sad...

---

### Post by shanepardue on 2008-03-28
> **wieman01 said:**
> It has issues with the latest version, the thread in Truecrypt's forum confirms it. Sad...
That's too bad..at least we can just downgrade to 5.0a until Hardy's final release. (If you can stand to wait until it's final release..hehe)

---

### Post by wieman01 on 2008-03-28
> **shanepardue said:**
> That's too bad..at least we can just downgrade to 5.0a until Hardy's final release. (If you can stand to wait until it's final release..hehe)
Tough one... ;-) I'll wait. I gives me occasional freezes, but usually continues after a few seconds/minutes. So the damage is somewhat limited.

I'll definitely go for Hardy.

---

### Post by chewearn on 2008-03-28
Thanks!  I will also wait for hardy, since it's less than a month away.

For the moment, I have reverted to 4.3a.  Since I have invested a bit of time polishing off a mount/dismount script a while back, the GUI is not that essential. 

Yesterday, I tried the 5.1a on a Xubuntu machine, the system locked up real bad when I was writing a file.  I have to ALT+SYSRQ+REISUB.  Then, the whole Xubuntu GUI broke upon reboot.  Took me a hour to figure out how to fix.

---

### Post by mkammerer on 2008-03-29
Got the same problem. After hangup the ubuntu gui was broken. What's the fix?

---

### Post by shanepardue on 2008-03-29
> **mkammerer said:**
> Got the same problem. After hangup the ubuntu gui was broken. What's the fix?
Please read this whole thread. There's a fix for version 5.0a.

---

### Post by mkammerer on 2008-03-29
I already know the fix for truecrypt. I wan't to know the fix for the broken ubuntu gui :)

---

### Post by chewearn on 2008-03-29
> **mkammerer said:**
> I already know the fix for truecrypt. I wan't to know the fix for the broken ubuntu gui :)

I have the problem in Xubuntu Xfce.  Not sure if this will help you for Ubuntu Gnome.

These were what I did:
1. Press ALT+F2 to bring up the Run dialog, then ran: "xfce4-panel".  This brought back my panel.

2. Go to: Applications > Settings > Settings Manager > Desktop; enable the checkbox "Allow Xfce to manage the desktop".  This brought back the desktop and background picture.

3. Delete everything under ~/.cache/sessions

4. Go to: Applications > Settings > Settings Manager > Sessions and startup; enable the checkbox "Prompt on logout"

5. Restart.

---

### Post by shanepardue on 2008-03-31
> **mkammerer said:**
> I already know the fix for truecrypt. I wan't to know the fix for the broken ubuntu gui :)
The only option is reverting back to an older version. 5.0a is a gui version. You can have a 
gui working in Ubuntu. Simply download 5.0a and use the fix mentioned in this thread.

---

