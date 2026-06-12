---
title: "How to change the default Xsession?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by rjc on 2006-08-04
Hello,

I use kubuntu with kdm, but since I need my machine for testing various things I also wanted and ubuntu environment, therefore I did an "apt-get install ubuntu-desktop". But since then the default session seems to be gnome, but I want it to be KDE. So how can I change this back to KDE again?

I've read something about the .dmrc file, but I don't know what to put into it, also there's no man page for the file.

Thanks for your help,
rjc

---

### Post by Drakkor on 2006-08-04
Try this: Log out>On the bottom left there will be an Options button,click that>Select Session, and there should be a list for you to select. I do this with XGL. :p

---

### Post by rjc on 2006-08-04
yes, this is correct, but I don't want to do this every time I log in. I want KDE to be the DEFAULT.

---

### Post by Drakkor on 2006-08-04
When you switch sessions, you should have a button on the right to make that the default session, or just for this session on the left.

---

### Post by rjc on 2006-08-04
also right, but only correct for gdm, and since I use kdm, this doesn't help me either :). Thanks anyway for your help. Any other Ideas? I guess I have to change this in a config file or there is an application which does this, which I haven't found yet.

---

### Post by abbeychase on 2006-08-18
YEah, can someone just answer the question?  i mean, the answer *should* be:
/etc/X11/xinit/xinitrc

but it isn't, because when i first installed i had the xfce4 window manager, which i didn't want, added "afterstep" to that file, and was still getting xfce4 as the default window manager...so, for those who will not use KDE (kdm) or GNOME (gdm), please answer the question so we can all benefit from someones good graces and knowledge

---

### Post by geek65535 on 2007-08-03
The default window manager is saved into a file called .dmrc in your home directory. There seems to be a problem (from my experience, anyway) with KDM modifying the file properly.

$ cat .dmrc
[Desktop]
Session=kde


The systemwide default window manager is controlled by the symlink in /etc/alternatives:
$ ls -l /etc/alternatives/x-session-manager
lrwxrwxrwx 1 root root 17 2007-07-02 17:00 /etc/alternatives/x-session-manager -> /usr/bin/startkde

The safest way to change it is: 
$ sudo /usr/sbin/update-alternatives --config x-session-manager

HTH,

Paul

---

### Post by fokukac on 2007-08-30
To change the display manager and to change the desktop manager is a different thing. To change the default diplay manager go ad edit the /etc/X11/default-display-manager file by typing:

**sudo gedit /etc/X11/default-display-manager**

The contents of this file should be if you want to use kdm (KDE's own display manager):

**/usr/bin/kdm**

Or if you want to use gdm (GNOME's own display manager):

**/usr/sbin/gdm**

The default display manager however doesn't guarantee thet you get GNOME or KDE. Changing the default setting is quite simple (as described above by geek65535 ). You shoud edit the file he speaks about by typing:

**gedit ~/.dmrc**

If you want to use KDE, just change the line "Session=*whatever*" to *kde* (as geek65535 suggested), if GNOME, then change it to *gnome*

---

### Post by red0menace on 2008-05-05
> **geek65535 said:**
> The default window manager is saved into a file called .dmrc in your home directory. There seems to be a problem (from my experience, anyway) with KDM modifying the file properly.

$ cat .dmrc
[Desktop]
Session=kde


The systemwide default window manager is controlled by the symlink in /etc/alternatives:
$ ls -l /etc/alternatives/x-session-manager
lrwxrwxrwx 1 root root 17 2007-07-02 17:00 /etc/alternatives/x-session-manager -> /usr/bin/startkde

The safest way to change it is: 
$ sudo /usr/sbin/update-alternatives --config x-session-manager

HTH,

Paul

I recommend changing x-window-manager as well:
$ sudo /usr/sbin/update-alternatives --config x-window-manager

For instance, I use xfce4, so my x-window-manager should be xfwm4.

---

