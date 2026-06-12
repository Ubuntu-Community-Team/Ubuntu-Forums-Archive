---
title: "what's the command for the slab?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-07-04
i'm trying to add it to my openbox right-click menu.

---

### Post by urukrama on 2007-07-04
What is the slab?

---

### Post by Drakkor on 2007-07-04
I assume you meant fstab
```
sudo nano /etc/fstab
```

---

### Post by Drakkor on 2007-07-04
> What is the slab?
It shows your drives and partitions,and how they are mounted.

---

### Post by Rui Pais on 2007-07-04
Or could be the slab menu:
[https://wiki.ubuntu.com/Slab](https://wiki.ubuntu.com/Slab)
[http://ubuntuforums.org/showthread.php?t=208131](http://ubuntuforums.org/showthread.php?t=208131)
[http://ubuntuforums.org/showthread.php?t=469732](http://ubuntuforums.org/showthread.php?t=469732)

Or Slab hardisk recording (what ever that could be something for musicians):
[http://www.slabexchange.org/index.cgi?INDEX+whatis](http://www.slabexchange.org/index.cgi?INDEX+whatis)


@fuscia 
it depends on what slab exactly and how you install it...

---

### Post by mpeters on 2007-07-04
slabtop ? cat /proc/slabinfo ?

---

### Post by fuscia on 2007-07-04
i'm talking about the bigass menu, like suse's sled.

---

### Post by Rui Pais on 2007-07-04
> **fuscia said:**
> i'm talking about the bigass menu, like suse's sled.

how do you install it?

---

### Post by fuscia on 2007-07-04
> **Rui Pais said:**
> how do you install it?

i just used automatix.

---

### Post by fuscia on 2007-07-04
i just need to know what command i would type into the terminal in order to make it appear.

---

### Post by Rui Pais on 2007-07-04
> **fuscia said:**
> i just need to know what command i would type into the terminal in order to make it appear.

if you installed using automatix then must be a deb package.
you can open synaptic, search and select slab package and see it's properties (menu on right button of mouse). 
On Property window theres a tab named Installed files. 
Look there for installed files on bin or something that looks executable (not doc, share, etc.)


Have you tried open a terminal, type **sla** and then press tab to see what options do you get?

---

### Post by ButteBlues on 2007-07-04
It's a gnome-panel applet so as far as I know you can't just "run" it.

---

### Post by fuscia on 2007-07-04
> **ButteBlues said:**
> It's a gnome-panel applet so as far as I know you can't just "run" it.

yeah, that's what seems to be the case. oh well....

---

### Post by Rui Pais on 2007-07-04
well if don't use gnome you can set gnome-panel to full transparent, remove any applet except slab, set the position/size to your desire  and run it from terminal or openbox menu with 'gnome-panel'.. 
it's a little weird but i used to do that a while ago with xfce (didn't like xfce panel for some reason i don't even remember now...) and worked well.

---

