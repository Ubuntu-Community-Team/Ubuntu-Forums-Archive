---
title: "Sawfish Window Manager"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by wdbreen on 2006-12-28
Gday All,
I would like to change the GNOME desktop window manager to use sawfish instead of metacity, as i have a preference for a certain theme which relies on sawfish.
This is what i did so far but it doesnt work.

1. Installed sawfish package from the repositories and also default sawfish themes.
2. Logged off and changed the session to sawfish.
3. Logged on and got a huge "beep" and then nothing....!

Am i doing something wrong or am i going in the wrong direction?:( 

Wayne

---

### Post by moshuptrail on 2006-12-28
I'm just guessing, but you may be trying something that is pretty "advanced".

What others have done is change the whole desktop.  For example, I've switched to the Xfce desktop, and I even tried the KDE desktop for a while.  That's pretty easy.  It sounds like you are keeping Gnome, but changing something "under" Gnome that you expect to change the theme.  Wow!

---

### Post by moshuptrail on 2006-12-28
I would guess there must be some way to configure gnome so it references sawfish objects rather than the default.  Have you figured it out yet?

---

### Post by wdbreen on 2006-12-28
Not yet!  I have also messed with the sessions preference but dont seem to be having any luck with that either.

Wayne

---

### Post by TheOtherShoe on 2007-06-01
In case anybody else comes across this thread looking for a solution, I think I have found one.

Open gconf-editor and navigate to the settings for /desktop/gnome/applications/window_manager. Now change the value of the key "current" from /usr/bin/metacity to /usr/bin/sawfish. Log out, log in again, and enjoy!

---

