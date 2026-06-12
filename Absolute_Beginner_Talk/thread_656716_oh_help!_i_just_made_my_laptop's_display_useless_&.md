---
title: "oh help! i just made my laptop's display useless &gt;,&lt;"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by ijason on 2008-01-02
hey guys. 

i just messed up beyond the point of fixing without some help, but at least i'm sure it's a fairly generic process i'll need to do. here's the story :

i was trying to get my laptop to use a second monitor as an extended display, through the >Sys >Admin >Screens and Graphics menu. for some reason when i told it to use the second screen it reset my default screen to "plug-n-play" and dumbed it down to 640x480 after the reboot. so, i went back in and told it "generic LCD" and the proper resolution. after rebooting it worked fine. BUT i still wanted to use that second monitor, so i tried setting it up again... this time being particularly careful to update both my primary (laptop) and secondary displays to the proper resolution. after rebooting this time, i get garbled screen on my laptop...

good news is, the ubuntu boot screen loads up fine, it's just when the log-on screen loads that things turn crappy. how should i go about restoring order to my universe? boot off a live cd and restore from a not-too-old xorg backup (which, i have)?

---

### Post by Rocket2DMn on 2008-01-02
You can reconfigure X with
```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked questions about your hardware - answer as best you can.  On the resolutions questions, use TAB to move and SPACEBAR to select your monitor's max resolution and everything less.
You can get to a TTY with CTRL+ALT+F1
You might need to run
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by ijason on 2008-01-02
is there any way without having to redo the entire configure process? i feel like i really lucked out in managing to actually get it to work properly the first time.

---

### Post by Rocket2DMn on 2008-01-02
You can post the output of
```
cat /etc/X11/xorg.conf
```
From what I can tell, manually editing xorg.conf is not always very effective, but we can try anyway (if we see anything blatantly wrong).
Otherwise you can make a backup of your current one (even tho the reconfiguration makes one anyway)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` then run the reconfiguration.
If it fails, you can restore the backup with
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by Linuxratty on 2008-01-02
You can also ,at boot up..choose "redirect".

---

### Post by ijason on 2008-01-02
i fixed it by restoring a few-week-old xorg.conf :)

---

