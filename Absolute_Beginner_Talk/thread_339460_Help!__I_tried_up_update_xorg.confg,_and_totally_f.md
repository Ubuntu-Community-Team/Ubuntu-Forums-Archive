---
title: "Help!  I tried up update xorg.confg, and totally fubar'ed my rig!"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by steven_mckenz on 2007-01-15
I just installed Linux (and am completely new at this).

When installing it, the display drivers didn't install properly.  It didn't have the 1280x1024 resolution included, so I was unable to switch to it.  So I opened up the terminal and typed:

sudo gedit /etc/X11/xorg.conf

The xorg.conf file came up.  I saw there was a command I could do (can't remember it at the moment) that would rebuild the xorg.conf file.  I ran it, and it allowed me to choose the type of video card that I had (nv -> Nvidia GeForce 6100 onboard), and the resolutions.  I added the 1280x1024 resolution to it.  I then hit "OK", and all was well.

I then tried to restart GNOME w/:

sudo /etc/init.d/gdm restart


It restarted, but now I have zero display.  It's black, with a really really small line at the bottom, or sometimes it will show me a full screen of black, and slowly fade bits and pieces of it to white.  It's really weird.

So, now that I'm freaking out about ruining my brand new system, can someone help me out to get rid of this problem that I have just presented myself with?  ](*,) 

Aargh!!

Thanks!

---

### Post by steven_mckenz on 2007-01-15
Anybody have any tips?

I would just like to restore the xorg.conf file to the backuped file that it created when I remade the xorg.conf file, so that way I can get back in and try it again.  It's VERY stragte with what it's doing now, and I'd just like to get back to how it was before.

---

### Post by Henry Rayker on 2007-01-15
press ctrl+alt and F1, this should bring up a terminal. Enter your username and password.

From there, you can do a```
sudo mv /path/to/backed/up/xorg_file /etc/X11/xorg.conf
```

That should replace the new file you made with your old one.

---

### Post by steven_mckenz on 2007-01-15
Freaking awesome.  The terminal came up, but I'm not sure where it backed up at.  I'll look for it and see if I can find it and try it.

Thanks!

---

### Post by NeoLithium on 2007-01-15
If you don't recall about where you backed it up; this command might work as well:

```

sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf

```

---

### Post by meng on 2007-01-15
If you can't find a backup file (it could be /etc/X11/xorg.conf~) then see if this will do the trick:
sudo dpkg-reconfigure xserver-xorg

---

### Post by tc101 on 2007-01-15
I have a friend with almost exactly the same problem.  The problem is that even after Steven gets the old file restored he still won't have the resolution he needs.  Why did adding the new resolution mess up his system?

---

### Post by steven_mckenz on 2007-01-15
Awesomeness!

Thanks to all of you for the help.  I had absolutely no idea when I was trying to get a display, as it was totally fubar'ed, and I was afraid I was going to have to reformat and reinstall again!

I found the file, and reverted the xorg.conf file back to it.  

Now, if I may ask another question in this same thread: I'm trying to set up the resolution to being 1280x1024, but it's not showing up in the resolutions listing, and I've added the resolutions manually to the xorg.conf file, but it's still not coming up on the list.

Is there a step I'm missing that I need to do to make it work?

---

### Post by irish_flu on 2007-01-15
Can you cut and paste the section where you edited the xorg.conf?

---

### Post by meng on 2007-01-15
> **tc101 said:**
> I have a friend with almost exactly the same problem.  The problem is that even after Steven gets the old file restored he still won't have the resolution he needs.  Why did adding the new resolution mess up his system?
I can't explain exactly why, but this is one of the reasons why (for simple tasks like adding resolutions) the following is preferred over direct editing of xorg.conf:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Henry Rayker on 2007-01-15
You may want to try the ```
sudo dpkg-reconfigure xserver-xorg
```

When it gets to the portions about the video driver, select the proper module for your card, then select the proper resolutions. That should fix it (it has in every instance that I've attempted it in, at least).

---

### Post by steven_mckenz on 2007-01-15
> **meng said:**
> I can't explain exactly why, but this is one of the reasons why (for simple tasks like adding resolutions) the following is preferred over direct editing of xorg.conf:
sudo dpkg-reconfigure xserver-xorg

But for me, whenever I run that program and add to it 1280x1024 as the resolution, the whole thing goes fubar and I get a black screen that slowly fades to white, with zero text or anything for me to read.

---

### Post by meng on 2007-01-15
> **steven_mckenz said:**
> But for me, whenever I run that program and add to it 1280x1024 as the resolution, the whole thing goes fubar and I get a black screen that slowly fades to white, with zero text or anything for me to read.
I see, but from your OP it sounds as though your other method was just as unsuccessful. Have you thought about installing the nvidia drivers instead of using the nv drivers?

---

### Post by steven_mckenz on 2007-01-15
> **irish_flu said:**
> Can you cut and paste the section where you edited the xorg.conf?

I have edited the "Section "Screen" ".

I added "1280x1024" in each mode before the other resolutions.  I have also tried adding the "1280x1024_60" instead of that.  Both times, it doesn't work.  It still automatically sets my resolution at 1024x768 when I boot Ubuntu up.  But if I try to run the dpkg line, and select 1280x1024, Ubuntu cracks when I reboot, and I get really really weird stuff on the screen (example being a black screen that very slooooooowly fades to a white screen in random spots of the screen).

---

### Post by tr333 on 2007-01-15
> **steven_mckenz said:**
> The xorg.conf file came up.  I saw there was a command I could do (can't remember it at the moment) that would rebuild the xorg.conf file.

IIRC, the command you had was ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Henry Rayker on 2007-01-15
I would recommend using the ```
sudo dpkg-reconfigure xserver-xorg
``` and, if it messes your xorg again, compare the two xorg.conf files ```
diff /path/to/backed/up/xorg.conf /etc/X11/xorg.conf
``` At least this way, we can try to pinpoint the errors...

---

### Post by gl0wst1ckn1nja on 2007-08-06
you can also do this.

boot from the disk you made

mount the hdd

terminal: sudo cp /etc/X11/xorg.conf /media/(mounted hdd)/etc/X11

and reboot booting from hdd

enjoy

---

