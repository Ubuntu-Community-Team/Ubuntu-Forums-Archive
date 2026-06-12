---
title: "System Restore"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-26
Is there a "System Restore" or "I'm a dumb ***" command to undo things done in terminal?

---

### Post by taurus on 2008-01-26
What command did you run from a terminal?

---

### Post by durdensbuddy on 2008-01-26
this is one as an example
     
     sudo apt-get install build-essential automake1.9 autotools-dev bzr libxdamage-dev   
     libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev  
     libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 
     libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common 
     python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev

As well as various other install directions related to the following walthrough  [http://ubuntuforums.org/showthread.php?t=659317&highlight=configure+ccsm](http://ubuntuforums.org/showthread.php?t=659317&highlight=configure+ccsm)

so far nothing broken, but I can see problems coming  through ignorance, so looking for some security.

---

### Post by taurus on 2008-01-26
You can just uninstall whatever you want with

```
sudo apt-get remove *package_name*
```

---

### Post by durdensbuddy on 2008-01-26
Thanks.  P.S. Installing AWN is giving me some hassles any tips?

---

### Post by LaRoza on 2008-01-26
[http://ubuntuforums.org/showthread.php?t=678665](http://ubuntuforums.org/showthread.php?t=678665)

There will be hopefully.

---

### Post by sailor2001 on 2008-01-26
that's the ONLY thing I miss in windows..system restore....

---

### Post by LaRoza on 2008-01-26
> **sailor2001 said:**
> that's the ONLY thing I miss in windows..system restore....

Windows uses a central registry (a big binary file that is easy to corrupt.) to help prevent the unauthorized use of programs. It used to be that programs stored their data in .ini files (sort of like what Linux does)

System Restore just backs that up.

Most viruses attack the registry because it is so fragile and easy to mess with.

My system restore program is attempting to do the same thing as Windows System Restore (see the thread I linked to).

I accidently deleted my code earlier (:)) but was able to get it back by decompiling the assembly file.

Hopefully, this app will be useful.

If you have any suggestions, what you want it to be able to restore, let me know.

---

