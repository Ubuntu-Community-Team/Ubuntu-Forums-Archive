---
title: "XGL is eating RAM - safe to stop?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-29
Well, the title says it all. It is taking up all my RAM. I am not using compiz-fusion right now so is it safe to stop it?

---

### Post by jan quark on 2008-02-29
I think you can remove the xserver-xgl safely without affecting the gnome session
(I have done this)
but you need to log in into the gnome session not the xclient session during login

let's wait what others have to say

---

### Post by lolzlolz on 2008-02-29
> **jan quark said:**
> I think you can remove the xserver-xgl safely without affecting the gnome session
(I have done this)
but you need to log in into the gnome session not the xclient session during login

let's wait what others have to say
i think it would be ok if u do what jan quark says, however stopping the process named xgl would i think kick you into command line interface which would force you to use startx to get graphical mode again, this is fine however as it is easy to get back

---

### Post by Hospadar on 2008-02-29
If you don't need any 3-d you can get rid of XGL.  I'm not sure it's a good idea to just stop it dead, you might want to go to a terminal and uninstall it.

I would do Ctrl-Alt-F1 for a text terminal.
Stop your xserver (gnome)```
sudo /etc/init.d/gdm stop
```Now uninstall xgl```
sudo apt-get remove xserver-xgl
```Now restart gnome```
sudo /etc/init.d/gdm start
```And this should dump you right back into gnome.  If not, try doing a Ctrl-Alt-F7 to get to the virtual terminal that runs gnome.  It may give you one of those errors and put you in the basic X settings mode, or just plain not start up at all.  If that is the case go back to your terminal (ctrl-alt-f7) and reconfigure your X server.```
sudo dpkg-reconfigure xserver-xorg
```

Worst case scenario you can always re-install xgl from the terminal if things don't work out.```
 sudo apt-get install xserver-xgl
```

---

### Post by forrestcupp on 2008-02-29
Just uninstall it and reboot, or restart X with ctrl-alt-backspace.

I assume you're using an ATI card.  If you want to use compiz, you could try [Envy](http://albertomilone.com/nvidia_scripts1.html) to install the latest drivers which supports compositing with aiglx, which means you don't even need Xgl.  There is plenty of help in many other threads on getting it working if you have problems.

---

### Post by intense.ego on 2008-02-29
I may not have described it correclty so let me try again. I want to keep XGL (because once in a while I might want to show off compiz to some of my mates), but I want the ability to disable it and enable it on without having to reboot. I log in under regular "Gnome Session" and not "Gnome + XGL" or whatever it is called in gusty (that is what it was called in feisty).

---

### Post by ajgreeny on 2008-02-29
I run a second hard disk on my machine to use as a test-bed for things that just might break the system.  At the moment it is Mint 4 installed there, so basically a variation of ubuntu7.10.  I tried xserver-xgl on that for my ati 9200SE card and it was no good at all so I just uninstalled it and restarted x.  No problem, even if it breaks the current x session you can just start another, no need to reboot.  That's one of the many advantages of linux over XP or Vista

---

### Post by intense.ego on 2008-02-29
So, I could just close xgl from the system monitor without a problem?

---

### Post by ajgreeny on 2008-03-01
You could and it should be OK, but if you want to do it clean just follow what hospodar said earlier.  Even if it isn't necessary it will be a good learning experience for you.

---

