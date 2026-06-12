---
title: "Ubuntu Ultimate Gamers Edition won't install"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by try5 on 2007-04-17
I have now burned a total of ten dvd iso disks with different dvd burners and programs, and they all match the MD5sum. (Burns at 1x, slowest possible speed). On 5 different computers including one laptop, all of which will boot and install singlely with ubunti 6.10 or dual boot with XP without difficulty.
(Including a try with a complete blank hard drive as well).

To date, none of these computers can be installed with Ubuntu Ultimate Gamers Edition. All have the same stopping point where you try to install, and it tries to format or partition the disk, it either spins its wheel forever when letting it do it, or complains that there is no root system or root file system when trying to do it manually. There appears to be no "alternate" or text install capability. Everything I can find where other people have posted about a similar sort of problem, to date no one has answered with the solution. 
Let me repeat this, all of the posts with similar descriptions seem to have not been answered, unless I am missing that as well. The fact that I can not find an answer from these previous posts makes me concerned.

The entire time I am thinking over and over that I must be doing something wrong. 
Now I am coming to the idea that maybe this "ultimate" is an April fools joke, which I am not finding very funny. I see no reason why this dvd should be able to load up like a live cd version  and work fine, but not install. If anyone has any information as to why I can't get this to work, a way to solve it, or something, I would appreciate it. I have other "wanting to leave windows" people who want this to work as well, and needless to say, having it not work after the hype is not good.
If it is an elaborate joke, okay you got me, please laugh at my expense and let me know so I can stop wasting my time on it.
Thank you.

---

### Post by jakev383 on 2007-04-17
I've never tried that one - it's not an official release (some guy just decided to make it), so you probably won't be able to get too much help; I googled it and see that almost all of the stuff that he installs is installable with a little bit of work. Maybe try something a little less ambitious, like his plain Ultimate edition, or just install the regular Ubuntu release and customize if yourself.
Sorry I couldn't be much more of a help. Is there a way to contact the author?

---

### Post by try5 on 2007-04-17
Thanks for the reply jakev353.

I had also tried the plain Ultimate version with the same results.
Normally I just use the Ubuntu 6.10 and install what I want. However, this gamers edition has various friends of mine wanting to try linux now and move away from windows....and they want this one because of the games and other software all preinstalled as most people in my area do not have cable or dsl. This would allow them to have a system they like without the hassle of never truely being able to update via the modem.
The idea sounds great, but it would seem it requires a little more work before it comes closer to being easier than windows. I know most people who use linux have nice high speed connections and have no idea how this version can make an impact of the people who would like a better option than windows, but without a good version that loads with minimal hassles I guess is still a while away. 
I am still a newbie myself, so creating my own install disk that would solve this problem is still beyond me yet.
Thanks again.

---

### Post by kelvin spratt on 2007-04-18
its possible that you have not left enough room on your hard drive to install as its rather large ultimate takes up as much as vista and gamers is half the size again just a thought

---

### Post by ibanezix on 2007-04-18
This is (unfortunately) a bug. See [https://launchpad.net/ubuntu/edgy/+source/ubiquity/+bug/40287](https://launchpad.net/ubuntu/edgy/+source/ubiquity/+bug/40287)

There is a way to bypass it:

When the operating system loads from the live cd, go to terminal and write:

```
sudo gedit /usr/lib/ubiquity/ubiquity/validation.py
```

This is a file written in Python, used by the installer. Towards the end of the file you will see the line:

```
if not root:
  result.add(MOUNTPOINT_NOROOT)
```

change it to:

```
if not root:
  pass
```

Then launch the installer and perform your installation. It should be fine.

---

