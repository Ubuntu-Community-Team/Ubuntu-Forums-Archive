---
title: "syncmaster 206bw - can't see anything anymore - want default monitor settings back"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-22
From the start of the installation I used my brand new Samsung SyncMaster 206BW (20 inch widescreen). The resolution was not the best, but I could install the driver that showed up.

The display even looked wide (not just stretched).(resolution now=1680 X 1050).

Then I went to -->System-->Administration-->Screens and Graphics.
Here I found that the screen registered on the computer was named "Custom1". Thinking it would be a good idea, I changed the display to the Samsung --> SyncMaster 206BW. Then it asked me to log off in order for the changes to take effect. So I did.

When starting now the nothing is really visible, total mess on the screen.


I also looked at the xorg.conf file - but in contrast to this [_user_]("http://ubuntuforums.org/showthread.php?t=658307") the resolution appears in it.

Now I only want to get the default, plug and play configuration back, how do I do that?

thanks,
ben

---

### Post by tojge on 2008-01-22
Have you tried ```
sudo dpkg-reconfigure xserver-xorg
```

---

