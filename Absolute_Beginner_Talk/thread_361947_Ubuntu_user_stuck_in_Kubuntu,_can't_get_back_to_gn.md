---
title: "Ubuntu user stuck in Kubuntu, can't get back to gnome"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by skyhopper88 on 2007-02-15
I was checking out Xubuntu (installed with aptitude) then decided it wasn't for me and went back in to gnome and removed it. When I restarted x and tryed to log back in to gnome from gdm, the splashscreen never comes up and a grey box appears in the upper left coner leaving me with nothing. I exited to the command line and it was complaining about not having kdm, though I never had Kubuntu before this. Shrugging it off I installed kubuntu and was able to start it up. But I still can't get back in to gnome, which is what I want to stick with. I've tryed uninstalling kubuntu-desktop and uninstalling/reinstalling ubuntu-desktop and gdm. Right know the startup screen is Kubuntu's, GDM loads, but I can only get in to KDE. Any ideas?

---

### Post by chuckyp on 2007-02-15
On the login screen click on Session and change it from KDE to GNOME.

---

### Post by skyhopper88 on 2007-02-15
Sorry, I wasn't too clear. I am doing that, but when I boot into gnome

> When I restarted x and tryed to log back in to gnome from gdm, the splashscreen never comes up and a grey box appears in the upper left coner leaving me with nothing.

^That happens. I only see the ubuntu background and the grey box. KDE boots ok though.

---

### Post by gradedcheese on 2007-02-15
sometimes it's a problem with the (hidden) settings files in your home directory.  I'm not 100% sure that this will solve it, but you could try deleting them.  Switch to a text shell (Control+Alt+F1) and then:

```

cd ~
mkdir settings_backup
mv .gnome* settings_backup/

```

(ok, so move instead of delete just to be safe).  Now switch to a graphical login (Control+Alt+F7) and try to log in to Gnome.  If you're stuck with an X problem, you can restart X by pressing Control+Alt+Backspace

---

### Post by skyhopper88 on 2007-02-15
Didn't change anything, thanks though. How do I move it back? I suck at rationalizing command line syntax.

---

### Post by gradedcheese on 2007-02-15
ah, darn.  to move back:

cd ~
mv settings_backup/.gnome* ./

that says: move from settings_backup/ anything starting with ".gnome" to the directory I am in right now.  A plain "cd" or "cd ~" means "go to my home directory"

try this too: go to a text shell and run "startx", try to get in to gnome.  When that fails Control+Alt+Backspace to kill X, now you should see some (hopefully useful) error messages about the X session.

---

