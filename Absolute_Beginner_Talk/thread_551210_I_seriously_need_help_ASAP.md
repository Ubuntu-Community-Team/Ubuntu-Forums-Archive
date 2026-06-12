---
title: "I seriously need help ASAP"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by eamonn on 2007-09-14
So, a few of my effects in compiz had stopped working, namely, the 3d cube and film strip thing. So I did a google search on how to fix it. The following link came up:

[http://ubuntuforums.org/showthread.php?p=3358149](http://ubuntuforums.org/showthread.php?p=3358149)

It sounded like these people were having a problem very similar to my own. So, I followed drvista's advice. I did "first >>synaptic package manager>>install xserver-xgl" and, tried doing "second>>Restricted drivers>>install ati drivers" but I didn't have anything that was restricted, then I typed "dpkg-reconfigure -phigh xserver-xorg" like I was told to.

I don't think I changed anything. A menu with a bunch of stuff I didn't recognize came up so I got out of it. Hit "OK" and was brought to a screen that had a listing of screen resolutions. I saw "1024 by something" and because that was my screen resolution I hit enter on it.

I rebooted.

Now I get an error saying x-server wont work and that I don't have any screen detected. 

Is there anyway I can go back to my old settings and fix this problem? I would have to do it through the terminal because gnome won't even start up anymore.

---

### Post by PmDematagoda on 2007-09-14
I remeber having the same problem before, and in my last case I never solved it. But don't worry it doesn't mean your problem is unfixable. 

The last time I had that problem, I managed  to solve it by replacing the xorg.conf file with the last backup of the xorg.conf file.

I found the latest backup by using the command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After which I replaced the xorg.conf file with the backup and it started to work.

P.S. before you do this get a backup of your xorg.conf file!!!

---

