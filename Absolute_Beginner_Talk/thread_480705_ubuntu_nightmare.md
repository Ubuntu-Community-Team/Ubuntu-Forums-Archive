---
title: "ubuntu nightmare"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by mitch707 on 2007-06-21
i installed the nvidia drivers and restarted x and said x failed i try to reconfigure xserver and when it gets to selecting the color like 24bit and press enter and it brings me back to the commandline but it still see the xserver setup above me and i rebooted came up with a black screen pressed ctrl alt f1 and got to the command line then pressed ctrl alt f7 and it says xserver disabled please help im completely lost

---

### Post by Crafty Kisses on 2007-06-21
> **mitch707 said:**
> i installed the nvidia drivers and restarted x and said x failed i try to reconfigure xserver and when it gets to selecting the color like 24bit and press enter and it brings me back to the commandline but it still see the xserver setup above me and i rebooted came up with a black screen pressed ctrl alt f1 and got to the command line then pressed ctrl alt f7 and it says xserver disabled please help im completely lost

Hey Mitch,

So I think I see the problem, you might want to try to reconfigure your X server with a different command like the following one:

```
sudo dpkg-reconfigure xserver-xorg
```
This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Ctrl-Alt-F7 to get back to graphical mode and then Ctrl-Alt-Backspace to reset the X server (so your changes can take effect).

After you have reset and reconfigured your X server file you might want to back it up, so if anything ever goes wrong again you can recover it.
To back up your X server enter the following command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

You can then edit your X server file, by:
```
sudo nano /etc/X11/xorg.conf
```
From there you need to change the "nvidia" to "nv" and that might work.

Try also installing vesa drivers, I'm not too sure what version of Nvidia's card you have, but if you have an older one, you might want to install the vesa drivers when your prompted to, select the Vesa drivers, and hopefully this will solve your issue.

Make sure you pick **vesa** as a driver for your graphic card. When done, reboot with
```
shutdown -r now
```

---

### Post by samuraiCat on 2007-06-21
> **mitch707 said:**
> i installed the nvidia drivers and restarted x and said x failed i try to reconfigure xserver and when it gets to selecting the color like 24bit and press enter and it brings me back to the commandline but it still see the xserver setup above me and i rebooted came up with a black screen pressed ctrl alt f1 and got to the command line then pressed ctrl alt f7 and it says xserver disabled please help im completely lost

Ha! I just did that the other day. Go here: 
[http://ubuntuforums.org/showthread.php?t=479398](http://ubuntuforums.org/showthread.php?t=479398)

---

### Post by mitch707 on 2007-06-21
thanks for the help i used the dkpg command but i can restasrt x but i still get a black screen

---

### Post by mitch707 on 2007-06-21
ok it says something like xserved disabled something GDM and im just really frusterated right now

---

### Post by Crafty Kisses on 2007-06-21
This link may help you:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by mitch707 on 2007-06-21
if done all everything and xserver just keeps failing

---

### Post by Crafty Kisses on 2007-06-21
> **mitch707 said:**
> if done all everything and xserver just keeps failing

Then if this is the case, you might want to reinstall Ubuntu. I know it's harsh, but at this point I'm not really sure what's wrong. The reconfigure command should have solved your issue but you should do a "clean" install of Ubuntu. If the problem persists you might want to switch to a higher version of Ubuntu (If you don't have 7.04 already).

---

### Post by mtron on 2007-06-21
I think reinstalling might be the last ressort, but let's start with some logs. 

The most important for now is the file /var/log/Xorg.0.log

Please post it's content here , and we might be able to help you better.

---

