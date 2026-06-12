---
title: "Gnome \not work after trying to install ati driver"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by kdiggdy on 2007-06-20
Help please?:(
I was trying to install the drivers for my ati card and I found a wiki 
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
I followed everything on there
I reboot put in the new gfx and restart, it loads the bios then \crash.
I took out the gfx then when it loads up it doesn't load up the graphical interface so i have to use prompt. I can log in and everything but it's useless to me since i have no clue on what i'm doing.
There was an error that said it was a problem with the
```
/etc/X11/xorg.con
```

In the wiki i edited the config with these 2 lines
```
nd add these lines at the end of the file:
File: /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```
So now i'm using liveCD, any suggestions?

Additonal info : running x86_84

---

### Post by phr0ze on 2007-06-20
Three options:

restore the backup of the xorg.conf you should have made.

or

Try
```
sudo dpkg-reconfigure xserver-xorg
```

Or 

copy the xorg.conf the live CD is using over the one on the hard drive.

---

### Post by Gen2ly on 2007-06-20
If those are the only two settings you changed then your xorg.conf is fine.  The only issue I can think of is if you have desktop effect running in which case you will need AIGLX enabled.

---

### Post by kdiggdy on 2007-06-20
none of the desktop effects would enable so i thought if i added the gfx card then they would enable.

> 
copy the xorg.conf the live CD is using over the one on the hard drive

How would i do this? 
run terminal haha i'm a newb i dont know the commands

---

### Post by kdiggdy on 2007-06-20
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

I replaced the config and took this line out and it works just fine now.
So how would I go about installing the ATI driver now?

---

### Post by samuraiCat on 2007-06-20
Ha! I did the same thing last night. I haven't tried to fix it yet, but here's the advice I got: [http://ubuntuforums.org/showthread.php?t=479398](http://ubuntuforums.org/showthread.php?t=479398)

---

