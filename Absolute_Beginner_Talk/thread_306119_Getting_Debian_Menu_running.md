---
title: "Getting Debian Menu running"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by ErrolRay on 2006-11-24
Used synaptic to get and install menu-xdg, but I cannot get it to appear anywhere.  If I use sudo apt-get install menu-xdg, it tells me it is already the latest version and doesn't do anything.
If I go to System, Preferences, menu layout, it is there but does not have a checkmark in the box, and won't let me put one there.  I am new to edgy, so be gentle.
Is there a way to use the Deb menu in Edgy>
Thanks,
Errol
:confused:

---

### Post by Spin Doctor on 2006-11-24
From my experience, the menulayout program is slow to interact with. When u have the menulayout program started, Click once on the program you want to add to the menu, and wait for a little while to have it process, and see if that helps. 
 
Sometimes it even helped me to close down the menulayout program, after a change made, and then open up the menulayout once again to see the changes taken place. Try it. It might work for you aswell!

---

### Post by ewl1217 on 2006-11-24
You need to install menu, not menu-xdg. Use this command in a terminal:
```
sudo apt-get install menu
```
Of course, you can use Synaptic if you want, but that's the quick way.

---

### Post by xpod on 2006-11-24
I use the Debian menu in Dapper but i too had issues with it in edgy....

I installed it from Automatix2 but it dont show up in edgy for some reason.
Even going into the menu editor has no effect.

I`ve tried re-installing it but sometimes it dont even appear in the menu editor let alone the actual menus.
And when it does appear in at least the menu editor i cant do anything with the check boxes either.

I stopped bothering about it a while back.Forgot all about it till i seen this.

---

### Post by PartisanEntity on 2006-11-24
I had the same problem today infact, you need to reinstall the menu and the debian menu, these are the steps I followed in Dapper:

```
sudo apt-get install --reinstall menu
```

```
update-menus
```

```
sudo apt-get install --reinstall menu-xdg
```

```
update-menus
```

from here:
[http://www.ubuntuforums.org/showthread.php?t=288588](http://www.ubuntuforums.org/showthread.php?t=288588)

---

### Post by ErrolRay on 2006-11-24
Thanks Partisan,
That got it running.
Errol

---

### Post by flyking on 2006-12-18
Thank You.  Your post solved my problem too.
George

---

### Post by -sands-o-time- on 2007-03-10
Hi, thanks Partisan.
Im using Edgy and your code did the trick for me.

---

