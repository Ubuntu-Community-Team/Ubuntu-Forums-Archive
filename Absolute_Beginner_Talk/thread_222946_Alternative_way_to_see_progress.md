---
title: "Alternative way to see progress"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by useResa on 2006-07-25
[FONT="Trebuchet MS"]Hello everyone,

I am currently installing Linux Desktop and it looks like the installation has come to a stand still. 
It stopped at 15%. The text below the progress bar is: "*Creating ext3 file system for / in partition #1 of IDE1 master (hda)...*".

Is there a way that I can check if there is still any activity or should I start all over?
[/FONT]

---

### Post by BoneKracker on 2006-07-25
The most common reason I've seen installations hang like that are corrupt download or bad cd burn.

By now, I'm sure you've terminated it.  Try it again if you haven't.  Maybe twice.

If it's still hanging at the same point, it's likely one of the two reasons above.

If you did not download your own copy / burn a cd, then obviously this is not the cause.

---

### Post by Madpilot on 2006-07-25
When you first start the Desktop CD, one of the options should be "Check This CD" - that'll run a file integrity check on the CD. If that finds an error, the CD likely won't install properly.

It's worth using that check before you start the installation, because the install takes long enough even if it goes perfectly - having to restart because of a bad CD is irritating...

---

### Post by useResa on 2006-07-26
Thanks for your suggestions. I have checked the CD from the menu and no errors were found.

After this I retried the installation, but it "stops" at the same point (15%).

Any other suggestions to monitor the progress?

---

### Post by moma on 2006-07-26
Try this

1) Boot up using the  Dapper LiveCD.

2) When in LiveCD, start the terminal program (gnome-terminal) from Applications -> Accessories menu.

3) Start GParted (partitioning program) from command line. Type:
$ [COLOR="Green"]sudo gparted [/COLOR]

and create two (2) partitions for Ubuntu.

**Swap** (swap partition). 
Size should be 2 * the size of physical RAM in your PC. Minimum 256 MB. Format it as "swap" filesystem.

**/ (root partition)**, minimum 10GB.
Format it as "ext3" filesystem.

When in GParted, select a partition and press right-mouse-button. It will show you actions.  Press [Apply] to commit the actions.

If it still fails to perform the formatting, delete the entire partition(s) and press [Apply].  Then try to repartition again.
----------------------------

If it still fails, try to format the partitions from command line. 
[COLOR="Red"](replace /dev/sda2 and /dev/sda3 with correct partition names).[/COLOR]

$ [COLOR="Green"]sudo mkfs.ext3 /dev/sda2[/COLOR]
or
$ [COLOR="Green"]sudo mkfs -t ext3 /dev/sda2[/COLOR]

and for swap partition
$ [COLOR="Green"]mkswap /dev/sda3[/COLOR]

Then start the installation as usual by click'ing the [desktop icon...]("http://home.online.no/%7Eosmoma//tmp/ubuntu_inst3.png")
Un-check the "**Reformat**" option in the installation's "Prepare mount points" dialog.  
I mean [this dialog...]("http://home.online.no/%7Eosmoma//tmp/ubuntu_inst4.png")

// moma
   [http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

---

### Post by useResa on 2006-07-26
Moma,
Thanks for your suggestions.
I'll try them tonight and let you know the result.

This may also solve my other thread "Unable to partition disks"
(see [http://www.ubuntuforums.org/showthread.php?t=222905](http://www.ubuntuforums.org/showthread.php?t=222905))

Update Aug 10, 2006:
Never succeeded in getting the hard disk partitioned.
"Solved" the situation as described in the thread mentioned above.

Thanks for all suggestions made.

---

