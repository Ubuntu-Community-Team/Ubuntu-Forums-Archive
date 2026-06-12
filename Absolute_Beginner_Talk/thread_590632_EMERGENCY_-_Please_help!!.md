---
title: "EMERGENCY - Please help!!"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-10-24
I think I've really messed up my mother's system.

I installed a new HDD on her machine. I formatted the old one and tried to mount it as a secondary drive (talk about a complicated process!!!). After I went to "unmount" it - at least, that's what I think I did - I'm now prevented from accessing ANYTHING. I get an error message that reads as follows:

```

Could not open location 'file:///home/mills'
There was an error launching the default action command associated with this location

```

Please help. I'd hate to think that I have to start over with a format and fresh install.



While we're at it, maybe someone can help me with the original problem, at which I clearly failed. I was trying to come up with a way to make a "shared" folder that any user can view when they log in, kinda like a shared network folder. Ubuntu doesn't seem to have a way to do that, so I was trying to use the slave HDD for that purpose. The problem I was running into was that only my mother has administrative privileges, so only she can mount the drive, and her kids can't.

Please help!!!

---

### Post by doctorbighands on 2007-10-24
I realize it may help your assessments if I could retrace my steps and tell you how I got to this point. Let me try...

First, the new drive (the master, on which Ubuntu is installed) is /dev/hda
The old drive is /dev/hdb1

In the terminal, I entered
```

sudo mount /dev/hdb1 /

```

Then, thinking that I hadn't succeeded in my original task, I typed
```

sudo umount /dev/hdb1

```

I don't know what happened, or what's gone wrong. Hopefully this helps!!

---

### Post by kevdog on 2007-10-24
What part of this post qualifies as an EMERGENCY?? Please dont cry wolf -- it really ticks me off.

---

### Post by doctorbighands on 2007-10-24
> **kevdog said:**
> What part of this post qualifies as an EMERGENCY?? Please dont cry wolf -- it really ticks me off.

The part where I can't do ANYTHING on her computer. I think that counts.

Don't be a jerk. It really ticks me off. 

If you don't want to help, don't bother posting.

---

### Post by HermanAB on 2007-10-24
The best way is to start over - it only takes about 30 minutes for a complete install.

Plug everything in that you wish to use with the machine: Camera, printers, scanners whatever.  Ensure that if both disk drives are IDE and on the same cable, that one is a master and the other a slave.  Stick in a CD and install again.  Partition the secondary drive as /data or /export.  Ensure that there is a separate /home directory, make / at least 15GB and /swap at least 2x RAM size and have fun.

If you cannot manage it, get an easier Linux version such as Mandriva.

Cheers,

Herman

---

### Post by doctorbighands on 2007-10-24
> **HermanAB said:**
> The best way is to start over - it only takes about 30 minutes for a complete install.

Plug everything in that you wish to use with the machine: Camera, printers, scanners whatever.  Ensure that if both disk drives are IDE and on the same cable, that one is a master and the other a slave.  Stick in a CD and install again.  Partition the secondary drive as /data or /export.  Ensure that there is a separate /home directory, make / at least 15GB and /swap at least 2x RAM size and have fun.

If you cannot manage it, get an easier Linux version such as Mandriva.

Cheers,

Herman


*SIGH*

I'll re-install.

The only problem is that when I went to install it the first time, the second drive never showed up. I changed the jumper settings on each to ensure that one is master and one is slave, and they both show up in CMOS that way. When I try to install from CD, though, only the master shows up for installation.

---

### Post by Shazaam on 2007-10-24
Please post the output of this...
```
sudo fdisk -lu
```

and this...
```
mount
```

On your mount command you forgot to tell it where to mount....
```
sudo mount /dev/hdb1 /mnt
```

notice the /mnt.

---

### Post by doctorbighands on 2007-10-24
When I tried open the terminal window to run the fdisk, as requested, I got another error message:

```

Could not launch menu item
Failed to execute child process "gnome-terminal" (no such file or directory)

```

???

---

### Post by Shazaam on 2007-10-24
You got that from the terminal?
On your panel (taskbar)- Applications>Accessories>Terminal

---

### Post by doctorbighands on 2007-10-24
No, I meant I couldn't even open the terminal in the first place. When I went to Applications>Accessories>Terminal, that's the message I got. The terminal window didn't open.

---

### Post by dfreer on 2007-10-25
> **doctorbighands said:**
> I think I've really messed up my mother's system.

This is where a backup would've come in handy. PLEASE backup your data before doing anything potentially dangerous to your system, especially if you don't know what you are doing!

> **doctorbighands said:**
> While we're at it, maybe someone can help me with the original problem, at which I clearly failed. I was trying to come up with a way to make a "shared" folder that any user can view when they log in, kinda like a shared network folder.

You could've created a folder anywhere on the filesystem with 777 permissions (read, write, and execute for everyone), and then created a link to that folder on every user's desktop, or in each user's home directory etc.

> **doctorbighands said:**
> Ubuntu doesn't seem to have a way to do that, so I was trying to use the slave HDD for that purpose. The problem I was running into was that only my mother has administrative privileges, so only she can mount the drive, and her kids can't.

So there was two drives in this computer, I'm guessing a primary with the OS installed, and a secondary (possibly an external?) with data you'd like to share with everyone? This is simply an issue of not mounting the secondary drive correctly, and/or needing to give permission to mount the drive to the kids.

Obviously I'm a bit confused, but it seems like you then performed some magic, in which you installed a brand new drive and then formatted the original drive, and I'm not sure where the secondary drive from the original problem ran off to:
> **doctorbighands said:**
> First, the new drive (the master, on which Ubuntu is installed) is /dev/hda
The old drive is /dev/hdb1

In the terminal, I entered
Code:

sudo mount /dev/hdb1 /

Then, thinking that I hadn't succeeded in my original task, I typed
Code:

sudo umount /dev/hdb1

I don't know what happened, or what's gone wrong. Hopefully this helps!!

I'm a bit confused on your hard drive layout both before and after you started messing with things. So you'll need to explain that in detail if I'm to help you out further. Same with your error messages, it's hard to tell whether you just mounted drives wrong, or if you erased important data.

EDIT: BTW, an emergency indicates that immediate action is required to resolve the issue, before things get worse/irreversibly damaged. If anything, in your situation immediate action is quite the opposite of what you need. Just slow down, examine what the problem is and what the *correct* solution is, and then fix things. I imagine this wouldn't have happened if you had done the above in the first place.

---

