---
title: "Increasing size of TMP folder"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by jonnyfive on 2006-04-29
I recently downloaded a larger game for linux, but upon extracting I get an error.
"Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install................................. ................................................................................ ................................................................................ ................................................................................ .......................................................................Extractio n failed.
Signal caught, cleaning up"


I am quite sure the issue is that the tmp folder is not large enough because I had to correct a problem where there was too much stuff in the TMP folder preventing me from logging in. How do I resize it?

I am a newb so please give me step by step."

---

### Post by syg00 on 2006-04-29
I doubt that Ubuntu mounts /tmp separately. Try this from a terminal```
df -h
```I suspect you'll find the root (/) full - /tmp is included in that unless mounted separately; in which case it will be listed.
```
du / |  sort -nr | less
``` should give you an idea of where all the space is being (most) used.

---

### Post by jonnyfive on 2006-04-29
df -h gives me this

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7             1.9G  1.7G  179M  91% /
tmpfs                 221M     0  221M   0% /dev/shm
tmpfs                 221M   13M  209M   6% /lib/modules/2.6.12-9-386/volatile
/dev/hda8              13G  329M   12G   3% /home
/dev/hda1              15G   11G  4.1G  73% /media/hda1
/dev/hda5              26G   25G  1.6G  94% /media/hda5


Does that mean anything to you?
The other command gave me nothing but a blinking curser.

---

### Post by syg00 on 2006-04-29
[QUOTE=jonnyfive]Filesystem            Size  Used Avail Use% Mounted on
[color=red]/dev/hda7             1.9G  1.7G  179M  _91%_ /[/color][/quote]

That's your problem - /tmp is included in that.
How the hell did you get Ubuntu squeezed into a partition that small  ???.
If you are going to be looking at (big) games, that needs to be a lot larger - and maybe a separate mountpoint for /tmp.
Easiest might be a re-install - any diddling with "/" needs to be from a liveCD. Can be done, but there may be ancillary cleanup - like fstab.

> The other command gave me nothing but a blinking curser.Yep, it'll take a while ...   :-?
Won't be of much help anyway, given the above.

---

### Post by jack ruby on 2007-02-01
I need some help here, too.
I need to increase the size of my /tmp folder. I'm trying to burn a cd from songs that are on my ipod. I want to use rhythmbox, but when I try to do it I get:
"Could not find temporary space! 
    Could not find enough temporary space to convert audio tracks.  803 MiB required."
currently my /tmp folder is 600 and change MB.
How can I increase the space to 850 MB?
Help Please!

---

### Post by jack ruby on 2007-02-02
Ok, I've got it figured out. It's the root drive that is running out of space. The properties window in Ubuntu makes it look like 600 meg was all that was left in /tmp. Really that meant there was 600 meg left for everything!
So, all I have to do is get rid of stuff, or increase partition size with gparted!

---

