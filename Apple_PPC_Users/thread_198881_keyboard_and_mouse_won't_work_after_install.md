---
title: "keyboard and mouse won't work after install"
date: 2006-06-17
forum: Apple PPC Users
---

### Post by deniseeliza on 2006-06-17
I installed Ubuntu 6.06 from the alternate install CD, because the Deskop one would hang at a maroon screen before even beginning the install.

Anyway, I installed it and that went fine, but when I boot to Ubuntu the keyboard and mouse (both are USB) are unusable when I get to the login screen.

After doing some looking around, I decided to try the workaround suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=142987"), however, I can't seem to follow those instructions.  I can't manage to get into recovery mode; pressing ESC at any point does nothing helpful.  All I can do is either select L for linux, X for OS X, C for CD, or if I hit ESC for a while I get to a screen that has a "boot:" prompt.

So what do I do from here?  I'm running an iMac G5 rev b.

I am an almost complete Linux newbie, so I also need a little hand holding.

---

### Post by BoneKracker on 2006-06-18
Press escape to get the boot prompt.
Then type
```
linux single
```
This will log you in as root in a non-graphical mode.
If you keyboard is working at that point, you can proceed from there.

It might be that your X-windows configuration is bad.
You can try to correct that by running a configuration utility that works well with macs called xorgautoconfig.

You might have downloaded a bad .iso cd image or burned the CD too fast.  Did you verify the MD5 digest of the .iso, and did you burn it slowly (like 4x)?

---

### Post by deniseeliza on 2006-06-18
Thanks for your help.  I typed Linux single at the boot prompt and that got me to a command line where I could try the commands listed in that other thread.  Unfortunately, my mouse and keyboard are still non-functional at the GUI.

I tried typing xorgautoconfig but that is apparently non existant on my machine at this time.

I did not verify the ISO and I burned it at whatever my fastest speed is.  I will try redownloading the ISO and burning more slowly, and check back in.

Thanks for your help again.

---

### Post by nkbj on 2006-06-18
Maybe you've hit this bug: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45152](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45152)

(Try the workaround in there).

---

### Post by BoneKracker on 2006-06-18
hmm...  I can't get Xorgautoconfig either (maybe I'm remembering that from a different distro).  If the other link doesn't lead you to a resolution, say so.

---

### Post by deniseeliza on 2006-06-18
Fortunately, we've made some progress.  Unfortunately, it's not very much progress.

I redownloaded the ISO and burned it at the slowest speed it'd let me (8x) and then reinstalled.  

I then tried this workaround in that bug report linked upthread:

```
disable sound in gdm by setting

SoundProgram=/bin/true
SoundOnLogin=false

in /etc/gdm/gdm.conf
```

At that point, I could type in my username and password at the login screen.  Hooray!  Howver, after I typed that in, it took me to a dark maroon screen and after about a second of that, the mouse freezes and the system is entirely locked up.

I also found [this post]("http://ubuntuforums.org/showpost.php?p=817651&postcount=22") that has more steps to try, and I did those, but still no joy.

So at this point I am successfully entering my username and password but the system locks up immediately after leaving the login screen.

---

### Post by nkbj on 2006-06-18
Unfortunately you are hit by a kernel bug like many other G5 users. The problem is the snd-powermac module.

You can try another couple of things from 'linux single':

1. Make sure 'snd-powermac' is not included in the /etc/modules file.

2. Add this line to /etc/modprobe.d/blacklist:```
blacklist snd-powermac
```

---

### Post by deniseeliza on 2006-06-19
Thank you, that worked!

Now I just have to figure out how to get online... 

Thanks for your help, I'll check back in if I run into any more related problems.

---

