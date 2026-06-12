---
title: "xubuntu installation issues"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by trkstr67 on 2007-07-24
Yes,I am a noob.  With serious xubuntu noob issues...
I have an old 500 mhz gateway machine, 320 MB of ram. Somebody told me that xubuntu was the version I should use. 

I use the xubuntu Live CD, and it seems like every time I restart, the machine gets hung up in a different place. I was actually almost totally installed last night but then the installation prgrm got hung up at 97%. 

Anybody got any ideas?

---

### Post by w4ett on 2007-07-24
You might want to try using the Alternate Install CD:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

It uses a text based installer.

---

### Post by trkstr67 on 2007-07-24
OK, I have gone to the text based(alternate) as suggested...

I did get further than before...up to 67%(woohoo!!), but now it just sits there.  I don't know if it has froze or it is still working...

It is creating ext3 file system for / in partition #1 of IDE3 master(hde)...

Any clues? How long does this step take?  It has already been two hours.:confused:

---

### Post by Rocket2DMn on 2007-07-24
I suggest letting it go for awhile, esp. since you have an older computer.  If it fails to start up again and you think the cd is OK, it's possible your hard drive is corrupt.

---

### Post by trkstr67 on 2007-07-24
OK,I waited over 4 hrs.  Did not move.  I shut the machine off.  I restarted to go back into the text based installer.

Went back in and went thru the motions.  Got an error about a destrapping thing.  Froze up.  Restarted again.
Now it is 'stuck at 51% 

Now what?  Hard drive?

---

### Post by w4ett on 2007-07-24
One tool for your present and future arsenal of tools should be the GParted Live CD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It will format, create copy and test partitions on drives.....you migh try and format and create an ext3 partition.........But....sounds like you might have a dodgy HDD......boot into your bios and set the S.M.A.R.T. capability on for your system, and if there is a physical/mechanical defect it will USUALLY catch it.

---

### Post by trkstr67 on 2007-07-24
OK, I am downloading now...
How do I boot into my bios?
And what is this SMART capability?  How do you get to that?

---

### Post by Rocket2DMn on 2007-07-24
Every BIOS is different, and you only have a split second to hit the button when you turn on your computer.  Common keys are F2, F8, F12, and DEL.  It should tell you, though you may not be able to act fast enough - just reboot and try again in that case.
SMART capability is like built-in monitoring on that hard drive.  Sometimes it can tell when the drive is going bad and can warn you in advance when it thinks it is failing.  If you get a SMART warning about drive failure, you should IMMEDIATELY back everything up because the drive is probably about to kick the bucket.

---

### Post by trkstr67 on 2007-07-24
Yeah, everytime I get into this I get a diff error msg.  I think I am just going to use this gParted and/or prob replace the HD...

I could not find this SMART thing you were talking about ...

---

