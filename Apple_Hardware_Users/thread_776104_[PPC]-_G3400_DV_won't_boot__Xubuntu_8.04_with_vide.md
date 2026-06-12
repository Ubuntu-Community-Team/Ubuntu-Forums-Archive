---
title: "[PPC]- G3/400 DV won't boot  Xubuntu 8.04 with video"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-04-30
I have this G3 PPC 400Mhx imac, slot loading CD ROM, 20GB hard drive, 512MB ram that will not boot up. If I do not type Linux nosplash video=ofonly.....I can hear the hard drive wind down and the screen goes blank (before I even get to the xubuntu loading screen).

If I type in Linux nosplash video=ofonly and the second boot prompt, t eventually loads into a command line saying that there was no reume image.

I have set the date right, I updated it and upgraded it, I set the /etc/x11/xorg.conf right and also had aded under Devices, Driver      versa, I think it was versa or vesa one of the two.

Still will not work.....What now?

---

### Post by shgadwa on 2008-04-30
I also tried to reset the RAM....(Option+Command+R+P). It did not work. I have reseted other computers fine however...with this one, it did not work.......What now?

---

### Post by stream303 on 2008-04-30
Ok, is it this one:
[http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html](http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html)
or is it the one below it, the SE model?

Since these are pre-owned machines, have you zapped the pram to start off with a clean slate?
[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

Are you using the "alternate" install image, or the live-cd "Desktop"?  Have you tried both?

Don't worry about the resume image - that is normal because you haven't hibernated the machine - it looks for this at boot time, and if it isn't found, continues on as normal....

---

### Post by shgadwa on 2008-04-30
Yes, I think it is that one....I did reset the RAM though, it worked...I was pressing control not command. However, it still does not work.

I used the alternate CD...I have not had any luck installing with live CDs...tried it on both Macs and PCs.

---

### Post by stream303 on 2008-04-30
Ok, well we are getting somewhere with video=ofonly that allow you to get to a command line at least.  Does it attempt to go to the graphical gdm screen, or what is the last thing seen when it hangs?  does it say "busybox" or anything like that?

Also, do you still have the older Mac-os on it?  Or did you let guided partitioning "use the whole disk", or did you just try to install to "free space"?

---

### Post by stream303 on 2008-04-30
Also for completeness, even though you have 512mb of ram, if it is 3rd-party ram, sometimes this will cause hangs, without notifiying us of segfaults or signal 11's.  It works with the older Mac-os, but sometimes not with Linux.  Stranger things have happened in ppc-land. :)

Even though this does not look to be the case, you could try removing the 3rd-party ram, and trying again and crossing fingers. :)  At least it will rule this variable out.

---

### Post by shgadwa on 2008-04-30
[QUOTE=stream303;4845588]Ok, well we are getting somewhere with video=ofonly that allow you to get to a command line at least.  Does it attempt to go to the graphical gdm screen, or what is the last thing seen when it hangs?  does it say "busybox" or anything like that?

Hre is what it says:

Loading...Please waite

bod_init failed:EXPLODE

Screen init failed

Kinit: Name_to_dev_t... (a bunch more numbers and words...)  Knit: Trying to resume from /dev/disk/by (a bunch more numbers and words...)
Kinit: No Resume image, doing normal boot,,,


Then it asks for my user name and passwd, and I'm into the command line....?

---

### Post by stream303 on 2008-04-30
Aha!  We've come across this exact same issue in another thread from a Powermac user with an ati radeon, and are currently looking into it from an end-user perspective.  Perhaps you can help us find the solution.

One thing you can do is peruse your xorg log file:

```
less /var/log/Xorg.0.log
```

and see what it is hanging on.  We have tried numerous kernel parameters to get around this issue, but so far, no luck.

So....  if you want this machine up and running you can try Gutsy - but that has it's own problems as well.

Can you try the older Feisty 7.04?  It has about 6 more months of support left in it, so the majority of apps should be good enough for awhile, especially if you enable the backports repository.

There's no guarantee that it will work out of the box, but there are posted solutions in the archives, and may be a bit easier to work with for the time being.

---

### Post by shgadwa on 2008-04-30
What is the most current OS that will work on ym computer???? Would openSUSE work...seems though that they only have a DVD for powerPC...can I sue two Cds or no?

I spent HOURs trying to install gentoo only to find that it decided to lock up on me on step 7, while configuring the kernel.....hmm

---

### Post by SphereCat1 on 2008-08-22
Alright, I have this exact same problem. I'm trying to run 8.04 on my PowerBook G3 Pismo, and it gives me that exact same error.

This thread has been dead for a while, but hopefully someone will find it.

Here are the specs for the PowerBook: 400mhz, 1MB Cache, 194MB RAM, 10.1GB HD, 8MB Video RAM, DVD/CD Combo Drive

Please Help! :(
SphereCat1

---

### Post by tiresia on 2008-08-22
Do you have any PCI cards in your G3? If so, remove it and try to start again after resetting PRAM

---

### Post by SphereCat1 on 2008-08-22
I don't have any PCI cards.

---

### Post by SphereCat1 on 2008-11-22
Anybody else have any idea on how to fix my graphics issues? Could it be related to not having a PRAM battery?

Thanks in advance!
SphereCat1

---

### Post by stream303 on 2008-11-22
Be sure to check the read-only ppc archives.  You may want to look into installing the server version, and then upgrading it to an xfce4 desktop, especially with only 194mb of ram.  You already seem to have a system working, but perhaps a lighter graphics setup is worth looking into...

[http://ubuntuforums.org/showthread.php?t=511293&highlight=pismo](http://ubuntuforums.org/showthread.php?t=511293&highlight=pismo)

This seemed to ease the pain a little bit for pismo owners as it is a version of the DIY low-memory approach (works for ppc just as well)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

