---
title: "How to keep X from starting on boot?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Madman6510 on 2008-03-04
Is there any way I can set Ubuntu to not launch the xserver at boot, but without removing x itself (i.e, I boot into the CLI and press startx to get into Gnome).

---

### Post by JoshuaRL on 2008-03-04
You can always try booting into Recovery Mode and logging in.

---

### Post by p_quarles on 2008-03-04
> **JoshuaRL said:**
> You can always try booting into Recovery Mode and logging in.
Err, no, that's a rather bad idea for a number of reasons.

To stop X from starting automatically:
```
sudo mv /etc/rc2.d/S99gdm /etc/rc2.d/K01gdm
```
Then, when you want to start X:
```
sudo /etc/init.d/gdm start
```

---

### Post by steveneddy on 2008-03-04
While still logged in, hit the buttons 

**Ctrl+Alt+F1**

This will take you to one of the TTY screens.

Log in with your user name and password.

then to kill the x session type this

```

sudo /etc/init.d/gdm stop

```

This kills X.

To shutdown type in terminal

```
sudo shutdown -h now
```

When you log in, X will not start. You will have to type in the terminal screen, after you log in

```

sudo /etc/init.d/gdm start

```

---

### Post by Madman6510 on 2008-03-04
P, the terminal seems to enjoy giving me a ```
mv: cannot stat '/etc/rc2.d/S99gdm': No such file or directory
``` error when I try to do that. Are you sure that's the right command?

---

### Post by p_quarles on 2008-03-04
What's the output of this?:
```
ls /etc/rc2.d
```

---

### Post by Madman6510 on 2008-03-04
P: 
S05vbesave                   S20makedev        S89atd
S10acpid                     S20nvidia-kernel  S89cron
S10powernowd.early           S20powernowd      S90binfmt-support
S10sysklogd                  S20rsync          S95preload
S10xserver-xorg-input-wacom  S20vboxdrv        S98usplash
S11klogd                     S20vboxnet        S99acpi-support
S12dbus                      S22consolekit     S99laptop-mode
S12hal                       S24avahi-daemon   S99rc.local
S19cupsys                    S24dhcdbd         S99rmnologin
S20apmd                      S25bluetooth      S99stop-readahead
S20apport                    S30gdm

Steven: I did what you said, Gnome shut down, and I halted the system. Booted back up, but Gnome still came up... with a new glassy red theme?

How can I keep X from starting on boot, but keep the theme? I like it :p

EDIT: Oops, the theme was just emerald ( I didn't reboot).

---

### Post by p_quarles on 2008-03-04
Okay, I just misremembered the priority that Ubuntu gives to GDM. This should work:
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/D01gdm
```
Quick explanation of what this does: the file /etc/rc2.d/X##gdm is a symbolic link which represents the action and priority of the GDM (Gnome Display Manager) script. The prefix "S" tells the system to start the script. The prefix "D" tells the system to disable the script by default. 

Once you do that, you'll be able to reboot into a command line login screen.

---

### Post by Madman6510 on 2008-03-04
Ok, it seems to be working now, except for that the login prompt isn't displayed at boot (I have to type my username after "Starting local scripts", then enter password and type startx), but that's not a big deal for now. Ty for the help.

---

### Post by p_quarles on 2008-03-05
> **Madman6510 said:**
> Ok, it seems to be working now, except for that the login prompt isn't displayed at boot (I have to type my username after "Starting local scripts", then enter password and type startx), but that's not a big deal for now. Ty for the help.
Well, that's actually how it's supposed to work. It has to start all of the other stuff enabled in /etc/rc2.d before you can login.

---

