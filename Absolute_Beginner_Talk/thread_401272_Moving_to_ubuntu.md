---
title: "Moving to ubuntu"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by JimTheMagicJumper on 2007-04-04
So I've been having a few problems with windows lately and I've decided it's finally time for me to give linux a go. I've done some reading and I'm pretty confident I know what I need to do but I still have a few questions, they're pretty simple and I think I know the answer to most of them but it doesn't hurt to double check.

First of all I have about 200gb of stuff I'm going to want to move from windows to ubuntu. I have an external hard drive to do this with and was just wondering how I should format it. I presume fat32 would be the way to go but I've heard windows doesn't like fat32 if it's over 32gb, but is this just if it's for the partition windows is installed on? Would I be better off formatting as NTFS then using NTFS-3g?

Secondly I want to dual boot windows xp and ubuntu. I currently have about 300gb of stuff on my hard drive and I only want to use about 40gb for windows, what happens with the stuff that's already there? will it all get deleted or will 40gb worth of stuff remain, if so is it worth just doing a fresh install of xp since I won't need anything that's left on there?

Finally, once I've got ubuntu installed I need to set up my wireless connection. I've looked into doing this and it seems I'm going to need to use ndiswrapper and the required drivers, but since I won't be able to use the internet can I download these now and burn them to CD to use when I set up my wireless?

I think that's everything I need to know for now, I'll probably have a few more questions once I get everything up and running, but for now I'm looking quite forward  moving to ubuntu.

---

### Post by oilchangeguy on 2007-04-04
see:
[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by freesitebuilder on 2007-04-04
I was given some excellent advice on dual-booting here:
[http://ubuntuforums.org/showthread.php?t=362862](http://ubuntuforums.org/showthread.php?t=362862)

And there's a lot of very helpful stuff here:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by bcmiller on 2007-04-04
You may find that you need to format and start over with the windows partition.

I just ran into this problem because the hard drive was badly fragmented and the defrag left too many "unmovable" sections scattered throughout the disk.

---

### Post by Kisil on 2007-04-04
If you're dual booting, FAT32 is by far the easiest way to share, as it takes no configuration.  I have a 220GB partition that works just fine, though I think I formatted it from linux.  If windows gives you trouble formatting, you might try booting with the ubuntu livecd to format your drive, then switching back to windows to transfer.  You can make windows play well with ext, and you can make linux play OK with NTFS, but it's really not worth the trouble.

I'm dual-booting on two drives, and it was much easier to install windows that way.  Even on one drive, I recommend a clean windows install if you can, because you'll avoid partition problems and old age problems.  Just make sure both OSes are working before you delete your backup :).

I used Ndiswrapper this summer with a linksys card and it worked great.  You're right about the downloading problem - maybe you can put the files on your backup drive.

---

