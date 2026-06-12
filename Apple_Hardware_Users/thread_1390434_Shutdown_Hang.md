---
title: "Shutdown Hang"
date: 2010-01-25
forum: Apple Hardware Users
---

### Post by Regunirun on 2010-01-25
Hi,

I'm running Ubuntu 9.10 on my PowerBook G4 1.5Ghz, 1.5GB RAM, 2005 model.

Every time I try shutting down (that is, shutting down via the Gnome GUI), everything starts out great, until I get to a blank black screen with:

```
init: usplash post-start processes (3241) terminated with status 1
* Shutting down ALSA. . .
* Asking all remaining process to terminate. . .
```

Displayed. There is no blinking curser, no option to do anything. No timeout. Perma-stall.

Having tried this a few times, the only thing that changes is the process ID e.g 3241, as per the example above.

This happens every time, and I have the latest updates via the update manager.

Thanks in advance.

---

### Post by linuxopjemac on 2010-01-25
You might wanna play with the b43 module. If the kernel patch does not work, you might just want to remove the b43 or b43legacy module.

```
sudo rmmod b43
```

or with some force if it doesn't want to cooperate

```
sudo rmmod -f b43
```

[http://mac.linux.be/content/shutdown-reboot-freeze-after-karmic-upgrade](http://mac.linux.be/content/shutdown-reboot-freeze-after-karmic-upgrade)

---

### Post by migel_wimtore on 2010-01-26
Installing Lubuntu fixed this for me (ibook G4). 

"sudo apt-get install lubuntu-desktop"

---

### Post by Regunirun on 2010-01-26
Why should Lubuntu fix this? Whats wrong with Gnome?

---

### Post by linuxopjemac on 2010-01-26
it's also puzzling me :o

---

### Post by Regunirun on 2010-01-26
Well if it is a Gnome problem, then theoretically Kubuntu or Xubuntu should fix the problem.. But i'm just speculating. I'll test it out and report back my results.

---

### Post by thatguruguy on 2010-01-26
make absolutely sure you are using the latest linux kernel.  For whatever reason, my wife's eMac didn't update to the latest kernel automatically.  After going into synaptic and marking it for upgrade manually, it installed and fixed the b43 problem.

---

### Post by Regunirun on 2010-01-26
Thanks so much everyone, thatguruguy in particular!

After a quick 'uname -a', I discovered my kernal was .14, and that .17 had the patch that I was looking for!

[Lurker Reference: [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/476154]](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/476154])

This topic is closed!

(Although why my kernel didn't auto-update is a separate problem.. :D

---

### Post by migel_wimtore on 2010-01-27
Well installing lubuntu did fix this for me.Perhaps it installs the later kernal version? 
- Can power down successfully from lxde and gnome after lubuntu dektop install.

However, after doing a fresh install this morning i have found that using ext3 (over ext4) for /root and /home has taken care of the problem for me (for the time-being at least) without the need to install lubuntu. Which suggests it might not (only?) be due to the kernal.

Cheers.

---

### Post by Regunirun on 2010-01-30
> **migel_wimtore said:**
> Well installing lubuntu did fix this for me.Perhaps it installs the later kernal version? 
- Can power down successfully from lxde and gnome after lubuntu dektop install.

However, after doing a fresh install this morning i have found that using ext3 (over ext4) for /root and /home has taken care of the problem for me (for the time-being at least) without the need to install lubuntu. Which suggests it might not (only?) be due to the kernal.

Cheers.

It is definitely a kernel issue. Installing Lubuntu is unnecessary. The link in my above post shows the LaunchPad bug

Installing Lubuntu works, but is much more trouble than just updating the kernel is Synaptic.

---

### Post by migel_wimtore on 2010-02-04
Right, will do next time. 

Why does the Lubuntu trick work though? I only happened upon this by chance as i wanted a faster desktop environment on my old timer laptop. 

Its odd, having done a number of complete ubuntu installs over the last month i get slightly different results each time (on the same hardware) and sometimes i dont have the failed power down issue. Could it relate to how i partition the hard disk, as this is the only variable.

And ps: was wrong about the ext3/4 thing, shutdown again failed a few days later (as opposed to failing on the shutdown right after update instlall).

---

