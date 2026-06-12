---
title: "ntfs problem"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-04-02
I followed how to mount ntfs to read/write on boot up using [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

The partition mounted just like how it is suppose to mount.  The problem is that every once and awhile the ntfs does not mount.  I just restart a few times and it mounts for what ever reason.  This problem just surfaced again yesterday and today when I went to sit down to figure out the problem the ntfs started to mount again.

---

### Post by justin whitaker on 2007-04-02
> **endlessurf said:**
> I followed how to mount ntfs to read/write on boot up using [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

The partition mounted just like how it is suppose to mount.  The problem is that every once and awhile the ntfs does not mount.  I just restart a few times and it mounts for what ever reason.  This problem just surfaced again yesterday and today when I went to sit down to figure out the problem the ntfs started to mount again.

This is a problem with HAL, not NTFS. There is are several bugs around this issue on Launchpad. The good news is that it seems to be fixed in Feisty.

---

### Post by WelshChris on 2007-04-02
Hmm, is ntfs access completely reliable now?  I'll be honest, I haven't been keeping up with advances, but the last time I looked, it was in beta and not to be relied upon.

---

### Post by justin whitaker on 2007-04-02
> **WelshChris said:**
> Hmm, is ntfs access completely reliable now?  I'll be honest, I haven't been keeping up with advances, but the last time I looked, it was in beta and not to be relied upon.

It's up to 1.0, but still not completely reliable. The issue he seems to be having is the same one that I had, that is that the drive randomly mounts, and rebooting gets it to run (eventually).

---

### Post by ComplexNumber on 2007-04-02
> **endlessurf said:**
> I followed how to mount ntfs to read/write on boot up using [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

The partition mounted just like how it is suppose to mount.  The problem is that every once and awhile the ntfs does not mount.  I just restart a few times and it mounts for what ever reason.  This problem just surfaced again yesterday and today when I went to sit down to figure out the problem the ntfs started to mount again.
that guide is largely a waste of time. all you need is the following 2 components:
--------ntfs-3g packages (install via synaptic)
--------ntfs-config ([click]("http://flomertens.free.fr/ntfs-config/")). to install it, just either double click on it or go to where you've downloaded and enter the command:
sudo dpkg -i <name of package>

---

### Post by endlessurf on 2007-04-07
so I think I found the problem.  I am running xp and edgy on my laptop.  The last time i used xp i did not go through the normal shut down steps, I just shut the lid and walked away.  I came back later and had just been using edgy meanwhile my partition was not mounting.  I went back into windows and closed and shutdown everything correctly and my partition mounted again when i used edgy.

---

