---
title: "ps3 noob please help"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by d4rkdr34ms on 2008-02-27
I am a complete nooob. I know nothing bout linux. I put the Ubuntu 7.10 in the p3 but i need help in etting up the wireless and the screen resolution. I have the sharp aquos gamer hdtv but my linux screen is cut in half. i need serious help. i did reearch and i read ppl fixing it thru "nano' or somnething like it. i dont know how to use anything. i have been ueing windows all my life. so can someone please help me.

-d4rkdr34ms

---

### Post by meindian523 on 2008-02-27
Pentium 3 or PS3?

---

### Post by Crafty Kisses on 2008-02-27
> **d4rkdr34ms said:**
> I am a complete nooob. I know nothing bout linux. I put the Ubuntu 7.10 in the p3 but i need help in etting up the wireless and the screen resolution. I have the sharp aquos gamer hdtv but my linux screen is cut in half. i need serious help. i did reearch and i read ppl fixing it thru "nano' or somnething like it. i dont know how to use anything. i have been ueing windows all my life. so can someone please help me.

-d4rkdr34ms

If your installing Linux on your PS3, it would have to go something like this.

1st. You put your CD in, it will boot the Linux kernel.
2nd. It will be at a black screen, and you do the following command: ```
startx
``` That should give you the GUI, if that doesn't do it, try ```
sudo startx
``` 

Hopefully your talking about PS3. :lolflag:

---

### Post by igknighted on 2008-02-27
> **Codename said:**
> If your installing Linux on your PS3, it would have to go something like this.

1st. You put your CD in, it will boot the Linux kernel.
2nd. It will be at a black screen, and you do the following command: ```
startx
``` That should give you the GUI, if that doesn't do it, try ```
sudo startx
``` 

Hopefully your talking about PS3. :lolflag:

A better choice would be to start gdm, which in turn would start X.  NEVER use 'sudo startx', as you would load your DE with full root privileges.  Start GDM with this command: ```
sudo /etc/init.d/gdm start
```
If you start X using the startx command, you cannot shutdown/reboot from the graphical interface.  You can only log out and then shutdown via the CLI.

---

### Post by 3rdalbum on 2008-02-27
Press Alt-F2 and type:

```
sudo dpkg-reconfigure xserver-xorg
```

Click the "Run in terminal" checkbox, then press Ok.

Go through the setup program; you can probably use the defaults. When it asks you if you want to do videocard autodetection, go to Yes. When it asks you if you want to do monitor autodetection, go No, then try the "Simple" monitor configuration.

You'll need to restart after doing this. If it doesn't help, then try the "Medium" autodetection - I think that involves choosing resolutions and refresh rates. It's easier than it looks.

I haven't used Linux on the PS3, and it's a relatively new thing to do so the developers of the Linux distributions haven't perfected things yet on it. But I'm hoping that this should work adequitely to get you going.

---

### Post by Crafty Kisses on 2008-02-27
> **igknighted said:**
> A better choice would be to start gdm, which in turn would start X.  NEVER use 'sudo startx', as you would load your DE with full root privileges.  Start GDM with this command: ```
sudo /etc/init.d/gdm start
```
If you start X using the startx command, you cannot shutdown/reboot from the graphical interface.  You can only log out and then shutdown via the CLI.

Yeah, true.

---

### Post by d4rkdr34ms on 2008-02-27
well i  reinstalled ubuntu in the playstation 3, and the screen is not cut in half, but the screen is till small
im trying to get a 1920x1080 resolution, but its only giving me 576x384 resolution. any way to change this?

---

