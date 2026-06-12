---
title: "Ubuntu 7.10 Install Problem"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Chazaxl on 2007-10-29
OK, not sure if this is in the correct forum, still a beginner, therefore assume this is OK.

Ive tried the 7.10 live CD, however it just goes to a blackscreen, nothing happens.

I then downloaded teh 7.10 alternate CD and proceeded to install 7.10. I had no problems during the install, however when it comes to start in Ubuntu, it recognises GRUB, gives me options (if i press escape) and then starts booting and ends up with a blank screen.

Eventually everything loads, hard drive and CD activity stop, however all I see is blank screen, the same as when I try the live CD.

Any ideas?

Running XP4200 dual core AMD machine with Nvidia GTX 8800 graphics card. I tried setting the res is Grub down to 800x600, still nothing.

When I try and boot it seems to 'hang' at random places. The first was on the 'HDD - CD Rom ATAPI' which sounds odd as CD ROM is not to be HDD?

Then on some USB devices ...

I can then remove / add USB devices, it picks it (the system is 'live' and responsive) however I cannot get Ubuntu to load or startx.

I then tried to install PCLinuxOS, for some reason the Ubuntu 7.10 was still on the drive and booted agian, no PCLinuxOS at all.

Help?

Thanks.

---

### Post by Karti on 2007-10-29
Have you tried to access another terminal window, that doesn't require X windows?

If not when it has stopped booting up press Ctrl+Alt+F3. If you get to a command line login screen, then you can look at your /etc/X11/xorg.conf file and see what is wrong.

regards

K
;)

---

### Post by OldTimeTech on 2007-10-29
I think if you had used search and typed in "Gutsy Black Screen Problems" you would of come up with pages and pages.

My suggestion if you want to install PCLinuxOS, run gparted first and format your hard drive.

I really don't know why all the problems are happening with Gutsy, but I do know it's being worked on.

---

### Post by Chazaxl on 2007-10-29
> **Karti said:**
> Have you tried to access another terminal window, that doesn't require X windows?

If not when it has stopped booting up press Ctrl+Alt+F3. If you get to a command line login screen, then you can look at your /etc/X11/xorg.conf file and see what is wrong.

regards

K
;)

Thanks, tried a few keystrokes looking for a terminal, but didnt know exactly what. Ill try it again now and see what its doing.

---

### Post by Chazaxl on 2007-10-29
> **OldTimeTech said:**
> I think if you had used search and typed in "Gutsy Black Screen Problems" you would of come up with pages and pages.

My suggestion if you want to install PCLinuxOS, run gparted first and format your hard drive.

I really don't know why all the problems are happening with Gutsy, but I do know it's being worked on.

Thanks, I read a good few pages of problems, nothing seemed the same though :-(

How do I run GParted? Im in Windows now, can see the drive although XP doesnt seem to reconise much, apart from the 3 partitions that Ubuntu made ....

---

### Post by Chazaxl on 2007-10-29
Also, for what its worth, I have the same problem trying 7.04 with live CD, same black screen ....

---

### Post by OldTimeTech on 2007-10-29
[http://ubuntuforums.org/showthread.php?t=579761&highlight=Gutsy+gives+black+screen](http://ubuntuforums.org/showthread.php?t=579761&highlight=Gutsy+gives+black+screen)

might check this out!

---

### Post by OldTimeTech on 2007-10-29
gparted is part of Ubuntu, but you also can google it and download it and then burn it to cd (that's what I've done for use on other people's systems).  It's a very good, very fast way to format the drive and repartition it if you want to....it also will only format one partition if you need only one partition.

Are you loading the 64bit version on your machine or the 32bit version?  Your also running an older machine, possibly not enough Ram?

You might try 6.06 (it's the LTS version and see if it loads)

Sorry don't seem to be much help, I upgraded my machine and like every upgrade prior too it worked without problems

---

### Post by Chazaxl on 2007-10-29
OK, running in Ubuntu at the moment.

I had to do the following:

Start Live CD (AMD64) version and then use safe graphics mode and remove splash and xforcestart (or something like that).

I then had the live version running, first install crashed.

Did it again, now running, trying to download the newest Nvidia driver ..... just installing now.

My PC has 2 Gigs of RAM, so no, not that old. Dual core X4200 and latest GTX8800 Nvidia card.

So its running, but had to do a few mods along the way to get it running. Not sure Im happy with everything yet.

---

### Post by OldTimeTech on 2007-10-29
no one is ever happy with everything and that's why we always tweak...human nature..

---

### Post by Chazaxl on 2007-10-29
> **OldTimeTech said:**
> no one is ever happy with everything and that's why we always tweak...human nature..

Agreed,

Now, need to figure out Beryl .... got it installed, how do I actually start it?

---

