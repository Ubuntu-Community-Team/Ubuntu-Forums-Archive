---
title: "blank screen after enableing desktop effects"
date: 2007-06-10
forum: Apple PPC Users
---

### Post by zapcojake on 2007-06-10
Hello, I clicked on the enable desktop effects from the menu and now all i get is a brown screen.  Is there a way to disable this from the cli or something?  I did a dpkg-reconfigure on X but it did not help.  Thanks

---

### Post by tcrroadie on 2007-06-10
Try removing your Gnome session file.  I'm not completely sure if this will fix your problem but doesn't hurt. 

The Gnome session file is a hidden file in your home directory. 
```
rm ~/.gnome2/session

```

Then restart GDM with this command 
```

sudo /etc/init.d/gdm restart
```

Also, what is the model of your Mac?  Please include the graphics card used.  We may be able to edit your xorg.conf file to get Compiz/Beryl working properly.

---

### Post by zapcojake on 2007-06-10
Its an early G5 with a FX5200

---

### Post by tcrroadie on 2007-06-10
> **zapcojake said:**
> Its an early G5 with a FX5200

Ah ha.  That answers why you received a blank screen after enabling Desktop Effects (Compiz).

Unfortunately there is not a Nvidia video driver that has 3D support for the PowerPC platform yet.  There is one in the works though called Nouveau. 

[Nouveau open source 3D Nvidia driver. ]("http://nouveau.freedesktop.org/wiki/")  

Did removing the Gnome session file disable Compiz for you?

---

### Post by stmiller on 2007-06-10
> **zapcojake said:**
> Hello, I clicked on the enable desktop effects from the menu and now all i get is a brown screen.  Is there a way to disable this from the cli or something?  I did a dpkg-reconfigure on X but it did not help.  Thanks

This is a known compiz bug, and is not PowerPC specific. It's kind of hit and miss with trying different xorg options to see what you can do. But yeah as tcrroadie said, there is no 3D acceleration with nvidia cards at the moment for PowerPC.

---

