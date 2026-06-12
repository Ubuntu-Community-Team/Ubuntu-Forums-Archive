---
title: "Lost the desktop"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Northsider on 2008-04-07
I upgraded to 8.04 the other day and set up my dual monitors, which worked great.  However, after I rebooted I was sent straight to the console with no working desktop.  I think this is a problem with x-server?  I read another post which said to:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Is this something that I should try to do?

---

### Post by Michael.Godawski on 2008-04-07
> However, after I rebooted I was sent straight to the console with no working desktop.
Yes that is weird. So none of your monitors is working?
The command will try to reconfigure the xserver. It is worth a try.

---

### Post by Northsider on 2008-04-07
Sorry, I left an important bit out.  I turned on the compiz desktop effects and it asked me to restart my x, so I logged out and selected restart x.  this worked fine, but when I rebooted I get sent to the console, all text.  My moitors work, I just don't get a desktop., only the console

---

### Post by Michael.Godawski on 2008-04-07
Try to run the command. And tell us what has happened.

---

### Post by Northsider on 2008-04-07
I believe the problem arose when I tried to configure my dual monitor setup.  When I run the above command and then "startx" it brings me to the desktop (thankfully!).  But when I tried to setup the 2nd screen again and restart xserver I just end up back at the console.

---

### Post by Stang94 on 2008-04-07
Yeah also on 8.04 was loving it till today when i did a update after update was complete i restarted and was welcomed to a all black screen also on dual monitors I used envy to set up my nvidia card with twinview weird part was i tried everything only thing i could do was to reinstall ubuntu was also weird i could use compiz and zoom desktop out only thing i saw was the skydome and cubecaps probably was a quick fix but I still aint hip to linux yet still a work in progress lol

---

