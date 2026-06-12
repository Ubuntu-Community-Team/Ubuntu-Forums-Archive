---
title: "Compiz on eMac G4 with NVIDIA GeForce 2 MX"
date: 2010-08-16
forum: Apple Hardware Users
---

### Post by srojtas@me.com on 2010-08-16
How can I make Compiz work on this eMac?  It's the original, 700 MHz, 1 GB RAM, Ubuntu 10.04.  It was enough trying to get the xorg.conf file to show any video, but now I want to be able to use compiz so I can have a faster experience.

---

### Post by srojtas@me.com on 2010-08-16
OK I discovered the Nouveau drivers now, but do they work with this card and if it does, how the heck is it installed and used?

---

### Post by pzkfw on 2010-08-18
> **srojtas@me.com said:**
> OK I discovered the Nouveau drivers now, but do they work with this card and if it does, how the heck is it installed and used?

 Download nvidia drivers here: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) Put them on your desktop, which is /home/srota  CTRL+ALT+F1 to switch to terminal.  
```
  #sudo su (enter in password) 
#/etc/init.d/gdm stop 
#killall x 
#init 3 
#cd /home/srota 
#ls 
#sh nvidia*
 (follow its instructions)
 #shutdown -r now 
```

---

### Post by linuxopjemac on 2010-08-18
this won't work, we are working on PPC here...

---

### Post by Macalla on 2010-08-18
> **srojtas@me.com said:**
> How can I make Compiz work on this eMac?  It's the original, 700 MHz, 1 GB RAM, Ubuntu 10.04.  It was enough trying to get the xorg.conf file to show any video, but now I want to be able to use compiz so I can have a faster experience.

Actually compiz doesn't make for a faster experience, it just makes the GUI environment more dynamic and prettier, at the expense of speed.

First you need to make sure your GUI is fully hardware accelerated, using the correct drivers for your card.

I use glxgears as a benchmark and run it every time I tweak the xorg.conf file to see if I can milk any more fps out.

---

