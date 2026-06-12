---
title: "Xfce session problems"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2006-12-30
Hi,

On XUbuntu 6.10 (Edgy Eft), after changing window decorations using User Interface Settings, Xfce crashed.  

When I try to login normally Xfce crashes and throws me back to the login screen.  When I login in failsafe mode I can run xfce4-session from xterm but with lots of errors (see below).

When I try to run User Interface Settings or the Settings Manager Xfce crashes and I have to restart gdm and login in failsafe mode to be able to run my apps, which use the default X widgets.  

Where is the config file containing the windows style so I can change it manually and get XUbuntu up and running again?  Thank you.

Errors when I start xfce4-session: 

-------------------------------------------
It looks like dcopserver is already running.  If you are sure
that it is not already running, remove /home/x1a4/.DCOPserver_wendy__0
and start dcopserver again.
-------------------------------------------

X Error: BadDevice, invalid or uninitialized input device 169
   Major opcode:   147
   Minor opcode:   3
   Resource id:    0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
   Major opcode:   147
   Minor opcode:   3
   Resource id:   0x0
Failed to open device
kbuildsycoca running...

(xfce-mcs-manager:11643): Gtk-WARNING **: Theme file for justblue-0.21 has no directories

Thunar: Failed to connect to the D-BUS session bus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

** (xfdesktop:11666): WARNING **: Unable to initialize D-Bus.  Some xfdesktop features may be unavailable.
** Message: Orange **: Too small icon size, using static icon

(xfdesktop:11666): Gtk-WARNING **: Theme file for justblue-0.21 has no directories

20
20
** Message: Orange **: Build alarm list: Processed 0 events.
                  Found 0 alarms of which 0 are active.  (Searched 0 recurring alarms.))
Unable to register terminal service: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
DOUBLE-CLICK: 250 --> -1 THRESHOLD: 8 --> -1 /bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found

---

### Post by x1a4 on 2006-12-30
Nevermind.  Fixed it.

---

### Post by MkfIbK7a on 2006-12-30
may i ask how?

---

### Post by x1a4 on 2007-01-08
> **wert613 said:**
> may i ask how?

It seems that Xfce's list of available themes do not take into account the different types of themes (cursors, icons, widgets etc).  What happened was that I selected a cursor theme to be a widget theme.  

So, I manually edited ~/.config/xfce4/mcs_settings/gtk.xml to themes I know work correctly and restarted gdm: 

sudo /etc/init.d/gmd restart

Then, to avoid this in the future, I renamed the themes directories in /usr/share/themes to reflect what type of theme it is.

---

