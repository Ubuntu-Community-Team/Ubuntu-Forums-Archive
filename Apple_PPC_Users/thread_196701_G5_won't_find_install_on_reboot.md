---
title: "G5 won't find install on reboot"
date: 2006-06-14
forum: Apple PPC Users
---

### Post by bmckee on 2006-06-14
Boy, Ubuntu sure doesn't like my Apple hardware.
[img]http://ubuntuforums.org/images/smilies/eusa_boohoo.gif[/img]
The only way I could get my trayloader to boot was to install Breezy and update to Dapper, then boot the old kernel.

Now I install on my G5 1.6, reboot, choose linux at the yaboot prompt and it can't find the root partition.  Eventually it drops me to a Busybox prompt - '/dev/sda4 doesn't exist'
[img]http://ubuntuforums.org/images/smilies/confused.gif[/img]

Looking in Disk Utility in OSX the three partitions I set up for Ubuntu are there...   
So how do I get this thing back on track?

---

### Post by swartzfeger on 2006-06-14
[QUOTE=bmckee]Boy, Ubuntu sure doesn't like my Apple hardware.
[img]http://ubuntuforums.org/images/smilies/eusa_boohoo.gif[/img]
The only way I could get my trayloader to boot was to install Breezy and update to Dapper, then boot the old kernel.

Now I install on my G5 1.6, reboot, choose linux at the yaboot prompt and it can't find the root partition.  Eventually it drops me to a Busybox prompt - '/dev/sda4 doesn't exist'
[img]http://ubuntuforums.org/images/smilies/confused.gif[/img]

Looking in Disk Utility in OSX the three partitions I set up for Ubuntu are there...   
So how do I get this thing back on track?[/QUOTE]

My guess it may possibly be something in your yaboot.conf. Do a search in the Mac/Apple/PPC forum for 'yaboot.conf' and you'll see a three of my threads. Once I worked out my yaboot.conf issues I booted successfully.

---

### Post by bmckee on 2006-06-15
My search turned up a lot of issues, but  no clear answers (that I grokked anyway)

I've spent some time twiddling about with my yaboot.conf file, and trashed it completely a couple of times :-(  It's back at the state it was when I started now - I can boot OSX or a CD, but Ubuntu won't find /dev/hda4  

My problem seems to be related to this monster tangle of threads - see [http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
for starters.

SATA drives are coming up in weird orders - heck if I only have one how can it be anything but /dev/sda?   

I'm tempted to install 5.10 and then do an apt-get dist upgrade on this machine too....

If anybody has other suggestions I'm all ears, or a clear pointer on how to create a working yaboot.conf    I know which partitions are what, but I don't know which drive letters Ubuntu seems to be assigning.

I'd love to hear from someone else using a stock iMac G5 that has a working yaboot.conf

---

