---
title: "gnome/system seems a little slow?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by touser on 2006-08-21
Hello everyone, i have dapper running and am so far pretty happy with it. The only problem is that the whole desktop seems a little slow. Windows are slow to minimize and maximize, theres a bit of a lag when right clicking on programs, GIMP is especially slow... just navigating the menus is extremely frustrating, litting things like that. Now i am not sure if this is because of the resolution i am running (2560x1600) or if it is something else? My computer should be able to handle it (2x nvidia 7800gtx, A64 4400+, 2gb ram) running the latest k7 kernel in the repositories, and Nvidia driver 87.62. Would kde be a little faster, is there some option i need to turn on in the graphics drivers? I'm just not sure where the problem is because the Windows desktop was lightyears faster than this. Thanks for any help!

---

### Post by newbymick on 2006-08-21
It could the nvidia drivers.  Updating the kernel to 2.6.17-x caused a conflit with my drivers and slowed the system to a crawl.  Solution was to uninstall the nvidia drivers and then reinstall them.  

I think the 3rd party driver are or weren't compatible, but as soon as the old was removed and the new install all was sun shine again.

---

### Post by touser on 2006-08-21
Thanks for the reply newbymick, i have reinstalled the nvidia drivers and that didnt have any effect :(

---

### Post by newbymick on 2006-08-23
Did you uninstall the old ones first.  This was the problem that I had.  It worked for me.

Also, Java - you need the latest scripts when updating the kernal.

Are you running xgl - if not, don't bother with it.  The eye candy is just too much for me.

---

### Post by touser on 2006-08-23
I was running xgl/compiz but it was just endlessly annoying and really slowed the computer down overall. I did uninstall then reinstall the nvidia drivers a few times sense i upgraded from i686 to K7 kernel and had to reinstall. I think the type of performance i am experiencing is probably as fast as it gets in gnome? Does anyone have a gnome desktop that reacts as quickly as a fresh install of say windows xp? I doubt it..

---

### Post by bodhi.zazen on 2006-08-23
My gnome is faster then Windows XP. But not on Ubuntu.

In my experience gnome can be slow in Ubuntu.

Try:

1. An alternate, light weight desktop manager.

2. Shut down un-needed daemons & servers.

3. Ubuntu server install -> install gnome.

4. An alternate Distro (Zenwalk, Arch).

---

### Post by newbymick on 2006-08-24
I agree with Bodhi.zazen.  Ubuntu crashed and locked on my white box.  I now have FC5, which runs like a dream, especially since I have increased the ram to 1Gig.  Also, I have changed the PSU to 400 Watt, which sorted a lot of problems.  

Linux seems to be hardware reliant, as in some distros will work perfectly first time and some won't.  Unbuntu works fine on my laptop but not on the stand alone.  Madriva was a nightmare and SUSE 10.1 didn't work at all for me. 

Live CD's are fine, but because of the read time required for the CD, speed can't really be compared with a full install.

---

### Post by newbymick on 2006-08-24
You could also try this thread 

XGL and Compiz eyecandy: One thread to rule them all

---

