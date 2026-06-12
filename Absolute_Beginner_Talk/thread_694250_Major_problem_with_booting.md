---
title: "Major problem with booting"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by shacamin on 2008-02-11
I was doing a bunch of stuff on my computer (burning a CD, listening to music, on Firefox, Thunderbird, and Pidgin), when my computer froze. I thought nothing of it and restarted. However, when I booted up, I got the equivalent of a BSOD and it told me that X wouldn't start. So I restarted, and my computer automatically ran a fsck which it could not finish (it got about 50% through before exiting in stage 4). It then asked me to enter my root password, which I did, and it went through a slew of checks before opening up a terminal. 

Long story short, I can't run any commands, and it's always because

```
The command could not be located because 'usr/bin' is not included in the PATH environment variable
```

I can cd to /usr/bin, and I've done an ls | more on it, and all the files are there. I have no idea what to do, nor does my friend. We haven't changed any files, and I haven't done so before this all started happening. The only thing I could think of would be when I was trying to install a new graphics card, I changed xorg.conf a little to adapt, and I think I messed up at one point. But I don't think that was a  part of this.

I really need help. My computer won't start up until this is fixed. If it can complete a fsck, it should be fine. What can I do?

---

### Post by taurus on 2008-02-11
If you can't fsck your / during boot, then try to run fsck from the LiveCD.

```
sudo fsck -y /dev/sda1
```
_Assuming_ /dev/sda1 is where / is on the harddrive.

---

### Post by shacamin on 2008-02-11
Yeah, it is, but I can't find my CD...:(

Is there another way? Or should I start downloading?

---

### Post by taurus on 2008-02-11
Usually when fsck can't scan your disk, it would drop you into a shell and you can run fsck from there, manually.  

It doesn't work even if you run it like

```
/sbin/fsck -y /dev/sda1
```
Again, I assume / is resided on /dev/sda1.

---

### Post by shacamin on 2008-02-11
Apparently there were a lot of illegal blocks in inode 10650368, so it cleared the inode, and it fixed a few more. It then went back to Pass 1. I'm waiting for it to finish...

Rescaning for multiply-claimed blocks...and there are a few...

Scaning directories for inodes with multiply-claimed blocks...

Just went through a bunch of stuff. Now I have this:

```
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: ***** REBOOT LINUX *****

```

I'm going to do that. See what happens. Yes?

---

### Post by taurus on 2008-02-11
Yes, reboot as it told you to.

---

### Post by shacamin on 2008-02-11
Success!

Thank you so much, friend. You have saved my baby.

---

### Post by banuc on 2008-02-12
I had the same problem and did the same things that are written here. Now there is a text on my screen which says:
     Could not start the x server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.
                                                 <ok>
I don't even know what should I search for in the forum to solve this problem, so I ask instead...

---

### Post by taurus on 2008-02-12
> **banuc said:**
> I had the same problem and did the same things that are written here. Now there is a text on my screen which says:
     Could not start the x server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.
                                                 <ok>
I don't even know what should I search for in the forum to solve this problem, so I ask instead...

Look in /var/log/Xorg.0.log to see what's the problem is.  Otherwise, see if it works again after you've reconfigure your X server.

To view xorg log:
```
tail -30 /var/log/Xorg.0.log
```

To reconfigure X:
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by banuc on 2008-02-12
How do I say "ok" to that text?

---

### Post by taurus on 2008-02-12
Use either the Tab key or the left arrow key to highlight it and then Return key to except it.

---

### Post by banuc on 2008-02-12
It does not work. "ok" is written on a red rectangle and I cannot highlight it by tab or left arrow key.

---

### Post by banuc on 2008-02-12
I could not wait, turned off the computer and started again, now it is fine...Why did this problem occur? Is there a spesific mistake that I have done?

---

