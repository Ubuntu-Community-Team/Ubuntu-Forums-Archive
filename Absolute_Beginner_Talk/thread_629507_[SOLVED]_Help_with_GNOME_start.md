---
title: "[SOLVED] Help with GNOME start"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by leileicats on 2007-12-02
After logging in with my login name and password after the graphical Ubuntu logo appears. That logo stays on the screen and no window manager Nautilus is started.
I remember that I uninstall something in the Synaptic Package Manager, after the restarting the above problem appears. But I forgot what I had uninstalled.
How could I fix that? I'm a rookie to Linux. Thanks!

---

### Post by leileicats on 2007-12-02
After logging in with my login name and password after the graphical Ubuntu logo appears. That logo stays on the screen and no window manager Nautilus is started.
I remember that I uninstall something in the Synaptic Package Manager, after the restarting the above problem appears. But I forgot what I had uninstalled.
How could I fix that? I'm a rookie to Linux. Thanks!

---

### Post by leileicats on 2007-12-02
After logging in with my login name and password after the graphical Ubuntu logo appears. That logo stays on the screen and no window manager Nautilus is started.
I remember that I uninstall something in the Synaptic Package Manager, after the restarting the above problem appears. But I forgot what I had uninstalled.
How could I fix that? I'm a rookie to Linux. Thanks!

---

### Post by leileicats on 2007-12-02
After logging in with my login name and password after the graphical Ubuntu logo appears. That logo stays on the screen and no window manager Nautilus is started.
I remember that I uninstall something in the Synaptic Package Manager, after the restarting the above problem appears. But I forgot what I had uninstalled.
How could I fix that? I'm a rookie to Linux. Thanks

---

### Post by cotcot on 2007-12-02
You can boot in recovery mode. This is one of the possibilities in the boot menu.
This gives you the possibility to log in in terminal mode. You can then install the package you have deleted. I guess this is nautilus.
```
sudo apt-get install nautilus
```

---

### Post by bapoumba on 2007-12-02
No need to use sudo from recovery mode, the user logs in as root.

From the GDM menu, hit <CTRL><ALT><F2>, login with your regular login and pswd.
```
sudo aptitude update
sudo aptitude install ubuntu-desktop

```

Go back to GDM with <CTRL><ALT><F7> and login.

Edit: threads merged.

---

### Post by p_quarles on 2007-12-02
The first step would be to try to get some info about why the GUI isn't starting up correctly. You'll need to boot into recovery mode (from the GRUB menu), then you can type this:
```
less /var/log/Xorg.0.log
```
Look for anything interesting there, such as "such-and-such failed," "so-and-so missing," "cannot find *y*".
Note that you can also use the "failsafe terminal" session option from the graphical login manager. If you go that way, the above command will need "sudo."

To ensure that you have all the normal programs that come with the default Ubuntu installation, you can try this:
```
apt-get --reinstall install ubuntu-desktop
```
Again, if you use the failsafe terminal, you will need to use "sudo" with this command.

---

### Post by bapoumba on 2007-12-02
Merged in several similar threads. Please do not cross-post.

---

