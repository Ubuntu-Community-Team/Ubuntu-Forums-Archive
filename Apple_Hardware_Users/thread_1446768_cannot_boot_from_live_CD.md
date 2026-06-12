---
title: "cannot boot from live CD"
date: 2010-04-04
forum: Apple Hardware Users
---

### Post by odinwise on 2010-04-04
I've been searching online through countless threads and websites trying  to find an answer to my problem, but to no avail.  here's the deal:

main problem at present:  ubuntu 9.10 live cd will not boot.

first, I'd like to preface my problem with a short story about how this all got started (hoping it might be helpful in solving this problem).  I'm new to linux and several days ago I decided to triple boot my macbook with it.  didn't seem like a big deal, I'm pretty handy with computers in general, so why not.  did a backup, took all the precautions I thought were necessary, etc.  followed the instructions to the T from the ubuntu documentation site for triple booting os x/winxp/ubuntu.
and it worked.
then, as I was going through a bunch of commands in terminal to get all the drivers up and running, etc...I ended up logging into root and doing something relating to getting the sound working.  it was taking a long time, and I had to leave, ended up shutting the macbook.  when I came back later and rebooted, os x was gone, winxp was unbootable (this is a problem I know there's a fix to and intended to do so).  my first response was to get os x working again.
I ended up reinstalling os x SL over my previous installation (since I was unable to restore from backup due to a locked mybook for mac..lol) and os x seemed to work just fine after that with no data loss.  I deleted the linux partition and winxp started working again.

I figured I was back to step one...now to reinstall ubuntu...but alas!  the live cd will not be read and is unable to boot.

I'm running a macbook pro 5.3.

here's what I tried:  holding 'c' at startup.  holding 'option' at startup.  selecting the disc with startup disk.
I've also reset the PRAM/VRAM multiple times and repeated the process of trying to boot the cd.

results:  holding 'c' makes the cd spin...after a while the apple logo pops up and os x boots normally regardless that I'm still holding the 'c' key.
holding 'option' will show os x and winxp disks that are bootable.  no ubuntu live cd, but will show other bootable cds like winxp or os x install discs.
opening startup disk in os x will show similar results.  os x, winxp, and network startup.  no ubuntu.

the disk will mount in os x, but again is unbootable.

any ideas on how to fix this?  or what the central issue could be preventing the live cd from booting?

thanks in advance for any insight or help with this problem!  I've been pulling my hair out going crazy over this for the past 2 days.

edit:  I'd like to add that I've re-downloaded the ISO for ubuntu twice and burned several copies on new CDs just to make sure it wasn't a faulty download or disc.  does not seem to make a difference.

---

### Post by gilthethrill on 2010-04-05
Hello.

Make sure the iso disc your burning is done in Disk Utility on the Mac.

Here are the instructions.  Scroll down to he Mac section:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope this woeks for you.

---

### Post by odinwise on 2010-04-05
thanks for the response!

I used Toast for most of my discs.  I'll give that a shot tomorrow when I wake up....I know the one I previously booted in the beginning was made with toast (mounted).  but I will try that anyway and post an update if it helped or not.

---

### Post by odinwise on 2010-04-05
> **gilthethrill said:**
> Hello.

Make sure the iso disc your burning is done in Disk Utility on the Mac.

Here are the instructions.  Scroll down to he Mac section:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope this woeks for you.

tried this today after waking up.  it worked.  I feel a bit dumb for not trying this before...somehow in my first run before all this got started, the only way I could make it work was burning with toast.  anyway, this definitely worked for me!  thanks for the help! can't wait to get ubuntu up and running again :D

---

