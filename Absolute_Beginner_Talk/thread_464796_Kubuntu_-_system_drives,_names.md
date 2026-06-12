---
title: "Kubuntu - system drives, names?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Gary.M on 2007-06-05
I'm new here, moving over from Windows XP.

When I tried ubuntu (gmone desktop) it mounted all of the partitions on my system and displayed them on the desktop with their Windows names displayed.

I decided I preferred the Kde desktop and controls (better hardware interfaces) so have installed that. If I use Konqueror to browse the drives I see everything with the mountpoint shwoing, but I'd like to see the drive or partition name as well or instead. How do I achieve this?

Thanks in advance...

---

### Post by plcdfa on 2007-06-05
I don't fully  understand what you wanna achive, but maybe this helps: create one directory per windows partition and name them after the partitions' labels. You can create them anywhere in your file system. (I think by default the partitions are mounted in /media, but I prefer to use /mnt instead. But you can also use your own home directory if you like.) Then all you have to do is to edit the file /etc/fstab so that the partitons are mounted to the newly created directories. You don't have to understand fstab this time, just search for the name of the directory where they're mounted now and replace them with the new ones. (If you're curious tough read this: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) ) The next reboot you'll have those windows "drives" under the new directories. (Or run 'sudo mount -a'.) You can also symlink these dirs to your desktop to have the same effect as in gnome.

---

### Post by SomethingCronic on 2007-06-05
I think you've misread Garys question. If you mount a drive in GNOME (say, pictures). the drive icon will appear on the desktop with the name 'pictures'. In KDE, it will be something like "REMOTE SHARE //MEDIA....."  and you can't actually see what the name of the share is. It's not easy to rename these icons to just simple names.

---

### Post by indytim on 2007-06-05
Try:

System Settings -> Desktop -> Behavior -> Device Icons

Check off what devices you want to appear on the desktop.

If you are not staisfied with the default naming conventions for your partitions then you will need to:

create new folder(s) in /media aptly named *
modify your fstab to mount the devices to your newly created /media folders *


* see multiple postings on the boards for specific instructions on doing this (use search).
IndyTim

---

### Post by Gary.M on 2007-06-05
Hey there. Thanks for these replies... they are all good stuff and point me in the right direction. I'm new here, but have a solid background in PC/Windows stuff so now need to begin understanding the Linux world. This is like going back to the DOS command line again! I'll do some reading from the links you've given me, and play around.

Can anyone point me to the best online resource covering Linux at the command level? A quick look at Tuxfiles as linked above suggests there's plenty there?

THANKS!

---

### Post by dwblas on 2007-06-05
keying df on the command line will give you a list of the device and where it is mounted, but doesn't know about any partitions that are not mounted.  As for  commands, you are using bash.  Here is a listing.  A Google for "linux bash commands" will give you more than you want to know
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
Man pages will tell you what options to use as well, so to find out what the "df" command will do, you would key in "man df"  Also, you might want to install sysinfo, as it will tell you what disk usage is, cpu info, memory, and a lot of other things that you may want to know later.  There are disk usage programs that display the info with graphics if you want to go that far.  Searching in synaptic for "disk usage" will probably point you in the right direction.

---

### Post by Gary.M on 2007-06-07
> **plcdfa said:**
> ...maybe this helps: create one directory per windows partition and name them after the partitions' labels. You can create them anywhere in your file system. (I think by default the partitions are mounted in /media, but I prefer to use /mnt instead. But you can also use your own home directory if you like.) Then all you have to do is to edit the file /etc/fstab so that the partitons are mounted to the newly created directories. 

Tried this and it did what you said and was very useful. Thanks!

---

### Post by plcdfa on 2007-06-07
Glad I could help.

---

### Post by Krusty Ruffle on 2007-09-25
So, what this thread is saying is that the icon names for remote mounts on the KDE desktop cannot be changed. The only way to simulate an icon with a shorter name that actually identifies the share at a glance is to turn off the icons for remote mounts and actually create simlinks to the mount points in the desktop folders.

Is that correct? 

If so doesn't that seem a bit painful? I mean, why give me a rename option in the context menu, and then let me go through all of the steps to rename it if it's going to have no effect?

Also, if I create the symlinks then what happens when I log into Gnome again, I have mout points showing up and symlinks to the same places. What if my network is down? normally the mount points wont show on the desktop, simply because they wont exist, but the symlinks still will. Missing icons are a big clue that something is wrong as soon as I log in, I like big clues....

Isn't there any way to modify some file or something that will just change the way that KDE names these icons, or give myself permission to rename them?

Or, have I missed the whole point of this thread?

---

