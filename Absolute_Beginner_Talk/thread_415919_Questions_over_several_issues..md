---
title: "Questions over several issues."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Stormweaver on 2007-04-20
Aight seems I have hit some walls again:


1. During start up I need to make the Grub screen not show the 386 version of the OS, this is on Server OS and it crashes by auto booting to the 386, I would just assume not have to stop GRUB each time to select what to boot.


2. The Nvidia seems to be holding its own, but I have no 3D enviroment, which I need for WoW and other things.... I know Ubuntu 386 Server doesn't accept GLX from Nvidia, but does that put an end to my 3D enviroment as a result?


3. I understand the running commands thing, but is it possible to set up a icon that simply opens Terminal already set in a directory other then /home ??

4. I got caught by the Bug that mutes sound during updates, went into the alsa mixer and turned it back on, now is that saved as is, or do I need to run a command before shut down or reboot to save that setting as is now???

5. Is Cedega really worth it?? I mean using it vs wine for installs?

---

### Post by Stormweaver on 2007-04-20
One update -- According to another thread I posted in, I am missing Open GL --- Thats whats causing the vid problems... So what can I do about this??

---

### Post by Jussi Kukkonen on 2007-04-20
> **Stormweaver said:**
> Aight seems I have hit some walls again:


1. During start up I need to make the Grub screen not show the 386 version of the OS, this is on Server OS and it crashes by auto booting to the 386, I would just assume not have to stop GRUB each time to select what to boot.
You'll need to edit /boot/grub/menu.lst. It's pretty well commented, but be careful, and make a backup of the file before editing. You'll need to set *default* variable to either the kernel number you want (0-n) or "saved". Saved means the last booted kernel will always be the default.
> 
3. I understand the running commands thing, but is it possible to set up a icon that simply opens Terminal already set in a directory other then /home ??

Sure. How that's done depends on your terminal. gnome-terminal would work like this:
```
gnome-terminal --working-directory=/media/music
```
Put that in a launcher (which you can create by right clicking on the Desktop).

---

### Post by Stormweaver on 2007-04-20
Aight seems I have hit some walls again:


1. During start up I need to make the Grub screen not show the 386 version of the OS, this is on Server OS and it crashes by auto booting to the 386, I would just assume not have to stop GRUB each time to select what to boot.   ---- FIXED


2. The Nvidia seems to be holding its own, but I have no 3D enviroment, which I need for WoW and other things.... I know Ubuntu 386 Server doesn't accept GLX from Nvidia, but does that put an end to my 3D enviroment as a result?


3. I understand the running commands thing, but is it possible to set up a icon that simply opens Terminal already set in a directory other then /home ??   ---- FIXED

4. I got caught by the Bug that mutes sound during updates, went into the alsa mixer and turned it back on, now is that saved as is, or do I need to run a command before shut down or reboot to save that setting as is now???   ---- FIXED

5. Is Cedega really worth it?? I mean using it vs wine for installs?



Just a couple more issues left, anyone have an idea that could help??

---

### Post by Stormweaver on 2007-04-21
2. The Nvidia seems to be holding its own, but I have no 3D enviroment, which I need for WoW and other things.... I know Ubuntu 386 Server doesn't accept GLX from Nvidia, but does that put an end to my 3D enviroment as a result?

--- This one has become a priority for now... The Nvidia is working, but after being refered back to take out the "dri" in the xorg.conf file, I attempted two different 3D programs and both caused a hard crash and lock up of Ubuntu... What files do I need to post from so that this issue can be resolved??

---

### Post by Stormweaver on 2007-04-21
Update: Checking in this morning, saw no replies.  Thought I might update whats gone on with it here since last post.

Per the Nvidia Forums, some took note of the "dri" still loading from xorg.conf.... I spent a bit with the file and only found one spot.


Load          "dri" 


is what it looked like, so I deleted it.  Next time I attempted to execute a 3D based program, system locked and the application crashed to desktop.  I ended up Cntl-Alt-F1'ing out of it , stopping gdm and restarting gdm to get it calmed down.


When I posted the new bug report they said "dri" is still loading.... I can't post the reports here as they are too big for upload and pastebin is not working.  So I don't know how to offer the info on whats going on.

If anyone can help - the others who have to this point have gotten me leaps and bounds closer to my goal, I just  don't know if I have messed up something or what.


I'm frustrated, don't know what to do.

Stormweaver

---

### Post by Stormweaver on 2007-04-21
Just bumping a bit as no one has responded.  If at this point I just need to give up on Ubuntu and this, someone please say so, so that I can try to find another OS to put on my server.


I know I must be frustrating people, and I want to learn about this, but I need this machine up and running so that what its supposed to be doing can be getting down while I start learning all I can about this.

---

### Post by luizfar on 2007-04-21
About Cedega, yes, it's worth it. Much better and easier to configure than Wine for games IMO. I don't use it tough, because I'm not really into games. Also, I can't tell you about licensing, I'm not sure if you have to pay for it or whatever, I just know that it's not open source.

---

### Post by Stormweaver on 2007-04-21
*Nod*

Big thing I need to figure out right now --- Why isn't 3D engaging???

What files can I post here to figure out why the 3D environment won't engage?


Stormweaver

---

