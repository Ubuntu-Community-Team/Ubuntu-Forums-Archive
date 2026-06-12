---
title: "[SOLVED] Terminal &amp;amp; Title bars missing"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Daveg4otu on 2008-03-24
Having had some problems I finally got Twinview working thanks to help of other posters here ....using  Nvidia Settings...setup is two monitors at 1280 x 1024  0 desktop across both - all fine there   so far ....but(**and  there is always a  but!)**.....


The terminal now opens only as a blank white rectangle - no prompts or menus.....and** all** title bars are missing from all windows.

I know there are workarounds - but would like to get things back how they should be.....
any help very welcome - but be warned ,,...this is only Day 3  for me and Ubuntu so please keep it  as plain as poss.   

:)

MTIA

Dave

---

### Post by jan quark on 2008-03-24
are you running compiz ?

when did the problem start to occur?

---

### Post by forestpixie on 2008-03-24
Are you running a nvidia card? If so try this in a terminal - but only for nvidia

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

then restart X by logging out and back in again and selecting "Restart X Server" from the login menu.

---

### Post by Daveg4otu on 2008-03-24
Jan - no idea what Compiz is....sorry.


F-P Yes  Nvidia Ti4200- will try your suggestion...BRB.

---

### Post by jan quark on 2008-03-24
compiz is this

[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)
[http://de.youtube.com/watch?v=M0RbWf5KUiY](http://de.youtube.com/watch?v=M0RbWf5KUiY)

stick with forestpixie 
I do not have nvidia on my laptop ...

---

### Post by forestpixie on 2008-03-24
Don't stick with me - I've got a pixie inside my monitor with a pack of crayons :D

---

### Post by Daveg4otu on 2008-03-24
F-P - sorry that's not working - maybe cos I'm not too sure what I am doing.....

I can open a Terminal by riunning xterm....then"sudo nvidia-xconfig" - then password. This produces the message

[B]
 Using X Configuration files: "/etc/X11/xorg.conf"
Backed up file "/etc/X11/xorg.conf." as  "/etc/X11/xorg.conf.backup"
New X  configuration file  written  to "/etc/X11/xorg.conf."[/B]

If I then type in...


**--add-argb-glx-visuals -d 24**

I just get a"Command  not found "response.

?

---

### Post by forestpixie on 2008-03-24
No - copy the whole command and run it as one. Then restart x

---

### Post by forestpixie on 2008-03-24
Hang on a minute - you'll need to get the old xorg back first

you can do this to copy backup to xorg

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

then run the command

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by Daveg4otu on 2008-03-24
You were too late with number 9 but no matter - I followed No.8 and it all seems to have worked OK - at least for now I have both title bars and the Term available from the  menu.

Thanks  a lot for taking the time to help.

Dave

---

### Post by forestpixie on 2008-03-24
If you've lost twinview you can go back by using the mv command I gave and then repeat the argb command.

Not a problem helping - just paying the favour to the forum :)

If you're finished with this can you mark the thread solved for others.

---

