---
title: "End of the installation Saga"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Mek-Eng on 2007-08-23
Well, I must say... the text-only installer of the Ubuntu was going quite well. So well, I decided to just leave it and come back in 10min when it was done. What I saw when I came back was a completely blank screen and a shutoff computer.

Now I don't think it's anything to do with the LINUX OS, but I turned off the PS at the back of the computer and turned it back on, roaring to life. But it no longer detected my hard-drive (which now smells a bit like burning plastic. YA... after all that farting around with the OS, the stupid hard drive decides to die. 

So... I'll try and get another hard drive and try again; I'll keep you posted.

---

### Post by Mek-Eng on 2007-08-23
I keep people posted and they don't even look.

:S :confused:

---

### Post by Aiello on 2007-08-23
I looked!
 I am hoping to install Ubuntu later today. Hope I don't get a fried HDD as well! [-o<

---

### Post by Steve1961 on 2007-08-23
> **Aiello said:**
> I looked!
 I am hoping to install Ubuntu later today. Hope I don't get a fried HDD as well! [-o<

You won't.  The hard drive problem is unlikely to be anything to do with Ubuntu.  Oh yes, I looked too.

---

### Post by WebSiteGuru on 2007-08-23
Well, I just saw this. I looked. Keep us posted. I have another system that only have 256MB RAM, so I probably need to do the same thing. Since I tried to load the LiveCD and it Freeze on me.

---

### Post by rexy on 2007-08-23
the live cd worked just fine for me on 250Mb(laptop with 16M internal memory). Combined with a slow harddrive(4200rpm) it takes awhile to boot it all up, but i managed to start the installer and it ran fine from there. It switched to a text base install at some point though, probably after a reboot?

isnt a freeze of the livecd more likely to be caused by a faulty X configuration at startup?

---

### Post by WebSiteGuru on 2007-08-23
> **rexy said:**
> the live cd worked just fine for me on 250Mb(laptop with 16M internal memory). Combined with a slow harddrive(4200rpm) it takes awhile to boot it all up, but i managed to start the installer and it ran fine from there. It switched to a text base install at some point though, probably after a reboot?

I am impatient. ;) I want it ZOOM ZOOM! :D

> **rexy said:**
> isnt a freeze of the livecd more likely to be caused by a faulty X configuration at startup?

How would I fixed this problem then?

---

### Post by rexy on 2007-08-23
well, uhm, this is going to be really obvious, but tell grub to not boot X.

not sure if the init command still work but edit the grub command line and say init=s or init=3 so it will  boot a different runlevel(without X)

---

### Post by WebSiteGuru on 2007-08-23
> **rexy said:**
> well, uhm, this is going to be really obvious, but tell grub to not boot X.

not sure if the init command still work but edit the grub command line and say init=s or init=3 so it will  boot a different runlevel(without X)

Not to a Newbies at Linux / Ubuntu. I don't even know how to edit grub command line.

---

### Post by rexy on 2007-08-23
[http://ubuntuforums.org/showthread.php?t=271800](http://ubuntuforums.org/showthread.php?t=271800)

try adding single or just 3 to the grub command line at boot, you can use the letter e to switch into edit mode, think it displays the help file too.

---

