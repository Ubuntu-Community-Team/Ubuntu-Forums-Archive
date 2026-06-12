---
title: "Screen res issue gone bad"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by sabatron on 2008-01-24
So I got a new monitor and I attempted to fix the resolution.  I ended up royally messing up and then the x-server couldn't find my graphics card. I've been browsing the forum for ways to fix it and I'm pretty sure all I have to do is change nv to nvidia.  All the commands that were listed were to be done from a terminal but I can't open one since technically I don't have a graphics card.  Can anyone tell me how to change nv to nvidia with just using the ctrl+alt+F1 screen at start up?

---

### Post by taurus on 2008-01-24
Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
```

Or you can edit /etc/X11/xorg.conf with

```
nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.

When you are done, reboot with

```
shutdown -r now
```

---

### Post by sabatron on 2008-01-24
I just rebooted in regular mode and it had the same problem...but I did change the driver from nv to nvidia..that part showed up.  What else can I do to set the GUI correct?

---

### Post by mr_ed on 2008-01-24
I didn't have to do any mucking around in xorg.conf at all.

I just opened up System->Admin->Restricted Drivers Manager and followed the prompts.

---

### Post by sabatron on 2008-01-24
I don't have a graphical interface so I have to do everything manually...I just want to be able to see my screen again...

---

### Post by mr_ed on 2008-01-24
Sorry about that.  I should have paid more attention when reading your post.

I would be tempted to leave it as nv for now.  The nv driver should work well enough to get your system back to a GUI, and then you could run the restricted driver manager.

I would back up my /etc/xorg.conf (ie. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak), and then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by sabatron on 2008-01-25
So last night I got frustrated and figured I'd fool around with it more this morning...I shutdown my computer and when I started it up this morning it took me to the Ubuntu log-in page (I've never gotten that far before).  I got hella excited and when I went to log in...I'd type my username and password correctly, and then it would look like it was loading my desktop....but then it would take me to the log-in page again...I'd type the correct info again...and it would do the same thing.  The good thing is it didn't take me to the "failed to start x server" error message that it used to...but now it won't let me log in...hmmmmm.  Did I break it?  I broke it didn't I...a friend of mine told me to just download the newest version of Ubuntu and install over this partition.  But I don't want to go through all the settings and stuff again.

---

