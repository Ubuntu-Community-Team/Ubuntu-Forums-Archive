---
title: "How to install GDM on kubuntu"
date: 2009-08-16
forum: Art &amp; Design
---

### Post by shanali4 on 2009-08-16
[SIZE=3]http://projects.gnome.org/gdm/

 How can i install Gnome Display Manager on kubuntu and replace KDE. Plz explian in detail. I m beginer linux uuser[/SIZE]

---

### Post by warreno on 2009-08-16
Have you looked [here]("http://www.mepis.org/docs/en/index.php/Replacing_KDM_with_GDM")?

N.b, when they say "as root" in terminal, what they mean is you should open a terminal window and precede a given command with the word 'sudo'. Borrowing from the page I linked to, they say:

```
apt-get install gdm
```What they mean is you should type this into your terminal window:

```
sudo apt-get install gdm 
```I *believe* part of the install asks you if you want to use KDE or GDM as your window manager. Select GDM. If you don't like it, you can always go back to KDM by selecting a KDM session from your login window's "Options" menu.

Hope this helps.

---

### Post by Bucky Ball on 2009-08-16
A much easier way for a new user is to go:

System->Administration->Synaptic Package Manager

Search for GDM, mark for installation and apply.

Either method, KDE won't be replaced but you have a choice at the login screen. Go to 'Sessions' and you should have Gnome as a choice of desktop environment.

---

### Post by warreno on 2009-08-16
> **Bucky Ball said:**
> A much easier way for a new user is to go:

System->Administration->Synaptic Package Manager

Search for GDM, mark for installation and apply.

Oh yeah. Forgot about that. To me, "easy" on Linux often means typing some things into a terminal window; I didn't think of the GUI side of it at all.

---

### Post by shanali4 on 2009-08-16
**Thank you all the contributors. My problem has been solved**

---

### Post by Bucky Ball on 2009-08-16
A pleasure, good news and welcome to Ubuntu and the forums.

ps: it is more trouble than it is worth trying to remove KDE. I'd leave it there or if you really want it gone, reinstall Ubuntu. Some have reported having dependency issues and other weird things happen when they have attempted to remove it. If anyone knows a foolproof, easy way of removing, please, let us know.

While you're playing around with desktop environments, you might like to try Xfce, the environment used by Xubuntu. Fast and simple; I use Gnome/Xfce 50/50. 

You can find it in Synaptics with a search for 'Xfce4'. Openbox is another interesting one; really pared back and minimal. Takes awhile to setup (time I have never spent but intend to eventually) but people seem to love it once they've done that.

Good luck and have fun. :)

---

