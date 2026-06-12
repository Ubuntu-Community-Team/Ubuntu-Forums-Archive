---
title: "Edgy broke down after an upgrade from dapper, how to repair?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by whee on 2007-01-08
I installed Dapper on my brothers computer and all seemed well.
I thought i'd upgrade to edgy and all seemed ok except for Nautilus which kept on crashing on bootup.
So after reading the forums i decided to upgrade nautilus via synaptic.
So i did that and it required a reboot, so i rebooted, but now X won't even start.
And there is only a garbly arcane looking error message which doesn't really say anything.
So my question is this.
Is there a possibility to fix/repair this by reinstalling edgy from a cd or by somehow reverting back to Dapper?
Repairing Ubuntu without a complete disk reformat would be preferred, so that i can keep things which were already installed on Dapper.

---

### Post by taurus on 2007-01-08
Can you get to a console by pressing <Ctrl><Alt>F2 while the screen is all messed up?

Log in with your username and password and see if X works again by reconfigure it.

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
Or reboot with

```
sudo shutdown -r now
```

---

### Post by whee on 2007-01-08
Ok i tried it and was able to get to a console.
But it didn't work.

At the end i got this error message: xserver-xorg is broken or not fully installed

---

### Post by taurus on 2007-01-08
From the console, run

```
sudo aptitude update
sudo aptitude install xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by whee on 2007-01-08
Ok that seemed to work.
X now starts and i'm able to log-in, but just when i expect the interface to load....only a brown screen loads and that's it.
It's the brown screen you get when you have no wallpaper on your desktop....nothing else seems to be loaded, apart from the brown screen everything seems to be blank...no trace of an interface whatsoever.

---

### Post by taurus on 2007-01-08
```
sudo aptitude ubuntu-desktop
```

---

### Post by whee on 2007-01-08
From the log-in screen i did Ctrl+Alt+F1 to get to a console.
Then i tried the above command, but it seems to display a list of command line flags (like -d -F etc etc) and at the bottom it says: aptitude does not have super cow powers .
Besides that it doesn't seem to download and/or install anything.

---

### Post by taurus on 2007-01-08
Sorry.  Forgot the install in there.  

```
sudo aptitude install ubuntu-desktop
```

---

### Post by whee on 2007-01-08
Ok tried it, but the problem persists. Only a brown screen shows up, but no interface.


PS: Sorry for the double post, i wasn't sure in what forum to post it.

---

### Post by taurus on 2007-01-08
Let's back up a little.  How did you upgrade from Dapper to Edgy?

---

### Post by whee on 2007-01-08
I used this tutorial:

[http://ubuntu-tutorials.com/2007/01/05/steps-to-upgrading-your-ubuntu-machine-ubuntu-6061-610/](http://ubuntu-tutorials.com/2007/01/05/steps-to-upgrading-your-ubuntu-machine-ubuntu-6061-610/)


So what consequently happened after the upgrade was first nautilus crashed on boot-up, then i tried to upgrade nautilus through synaptic, after a reboot x wouldn't start, then i seemed to have fixed   x with your help, but after that gnome-desktop wouldn't start.
And that's where we are now.

---

### Post by whee on 2007-01-08
Well i decided to wipe the partitions and install edgy from a cd instead of upgrading from dapper.
I'd like to thank you though Taurus, you've been a great help. Thanks!

---

### Post by amadeov on 2007-03-30
> **taurus said:**
> ```
sudo aptitude ubuntu-desktop
```

I'd had a hell of a time trying to figure this out... and this is what finally worked for me. 

I had updated from dapper to edgy using the "Method 2" from the wiki, and afterwards, I had a slew of errors that all resulted in me having no GUI.

After hours and hours of struggling, this is what FINALLY worked.  Thanks!

---

