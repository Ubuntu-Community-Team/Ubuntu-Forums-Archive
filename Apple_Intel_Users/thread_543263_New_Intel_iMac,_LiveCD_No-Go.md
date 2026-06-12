---
title: "New Intel iMac, LiveCD No-Go"
date: 2007-09-04
forum: Apple Intel Users
---

### Post by seanieb64 on 2007-09-04
HEllo everyone,

I've been blessed with a new iMac 20'. Been trying to get ubuntu too install,

I get the installer loading screen then a busybox who reports

```
cannot access tty - job control is off

(intrimfs)
```



Any insight what to do?

---

### Post by seanieb64 on 2007-09-04
Sorry,

Shoud have searched more, I'm gonna try this, I'll post back, btu I think this is the solution

> **dannyboy79 said:**
> UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to 
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command: 
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by seanieb64 on 2007-09-04
Okay, At the first step, booting up to the CD and adding break=top to the boot parems it works and dumps me to the command prompt, but the keyboard doesn't respond. :confused:

---

### Post by dchart on 2007-09-05
Which Live CD are you using? I had the same problem with Feisty, but Gutsy Tribe 5 works fine. i386, though; while both live CDs work, the amd64 install crashes out in X, while i386 works, and is what I'm using now.

---

### Post by cyberdork33 on 2007-09-05
> **seanieb64 said:**
> Okay, At the first step, booting up to the CD and adding break=top to the boot parems it works and dumps me to the command prompt, but the keyboard doesn't respond. :confused:
I use the alternate install CD as you are going to continually run into problems. You will find that x will crash on the live cd too. Is this one of the new aluminum iMacs? You may be the first to post on here with one. I have not seen that first issue you were having.

---

### Post by seanieb64 on 2007-09-05
Yeah, It's one of the new ones. dchart, Where are the repositories for Gutsy? Slipped my mind where to get the in-development releases...

EDIT Spoke to soon, I found it. Downloading it. dchart, Your instructions dont work for me, when I dump into the command prompt, it locks the keyboard, I cant input to the prompt. I'll try the Gutsy beta.

PS- Had any trouble finding the ATI driers for these new ones? what would I get for them?

---

### Post by cyberdork33 on 2007-09-05
> **seanieb64 said:**
> Yeah, It's one of the new ones. dchart, Where are the repositories for Gutsy? Slipped my mind where to get the in-development releases...

EDIT Spoke to soon, I found it. Downloading it. dchart, Your instructions dont work for me, when I dump into the command prompt, it locks the keyboard, I cant input to the prompt. I'll try the Gutsy beta.

PS- Had any trouble finding the ATI driers for these new ones? what would I get for them?

The new ATI linux drivers that support the Radeon HD 2400 are due out this week i believe.
[http://www.phoronix.com/scan.php?page=article&item=821](http://www.phoronix.com/scan.php?page=article&item=821)

---

### Post by seanieb64 on 2007-09-05
Damn, No aiglx support yet :(

But good news, I'm officially on Ubuntu  on my new mac :)

---

