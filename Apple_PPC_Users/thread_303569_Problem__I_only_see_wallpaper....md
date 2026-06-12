---
title: "Problem:  I only see wallpaper..."
date: 2006-11-20
forum: Apple PPC Users
---

### Post by BliND123 on 2006-11-20
Ok, I have xubuntu running on my Lombard.  I hadn't turned it on for about 2 weeks because I was just waiting for this wireless USB adapter...So, it gets here today and I turn on the notebook....I log in and after I see the mouse and mouse animation, I see wallpaper, and thats it, nothing more.  Just mouse I can move around on screen...what is wrong with it?  I tried to change session and did system default or xfce but nothing, same thing.

---

### Post by ssam on 2006-11-20
could be the [date bug]("http://help.ubuntu.com/community/UbuntuDateBug")

---

### Post by BliND123 on 2006-11-20
The date looks correct but I did what it said in the thing and still the same...What could it be?

Edit:  Is there some way (that wont take long, hopefully, and wont delete my files) to just like reinstall the desktop environment?

Oh yeah, and I just disconnected the power cable, and a bubble type message popped up saying it went to battery power.  So its sort of loaded up?

---

### Post by ajgreeny on 2006-11-20
Can you *alt+f2* to get a run command?  If so try opening up the gnome configuration program (I use kde and can't remember what exactly it is in gnome).  Perhaps something has gone crazy and borked your desktop, taskbar and panel that you can correct there.

---

### Post by BliND123 on 2006-11-20
Run program opens, but I am a noob, have no idea what command would be for gnome.

---

### Post by Ptero-4 on 2006-11-20
Blind123 is using xfce, hence the config app would be xfce-setting-show.

---

### Post by BliND123 on 2006-11-20
ah, yeah that made it open...hmmm, im going to mess around with stuff and see what could fix it.  Or tell me which specifically to go to?

---

### Post by ajgreeny on 2006-11-20
Sorry blind123. I missed the fact that you were on xfce, silly me!  I've never actually seen that in action, either, so will have to pass over to others to help, I'm afraid.
Good Luck.

---

### Post by BliND123 on 2006-11-20
Thanks anyways ajgreeny.  

Am I supposed to be able to open whatever that Panel is supposed to be?  Cause it wont open...all the other ones I have tried to open didn't fix anything.

---

### Post by BliND123 on 2006-11-20
Looks like #25 on this here had same problem...
[https://ubuntu.wordpress.com/2005/10/11/xubuntu-xfce-ubuntu/#comment-1156](https://ubuntu.wordpress.com/2005/10/11/xubuntu-xfce-ubuntu/#comment-1156)

Edit:  Hold up, looks like #28 said how to fix...let me try it.

Edit2: Nope, that xfdesktop command just changed my background (I have a list of like 30 I had added).  What else can I try?  If that didnt work then there is probably something wrong with mine?  How do I just reinstall the desktop thing...and not the whole thing again :P

---

### Post by BliND123 on 2006-11-20
Hey, ive been logging in and out and no luck...installed updates hoping one would somehow fix it but no luck.  I noticed something in the terminal...When I pressed Ctrl+Option+F1 to go to the terminal, I typed xfdesktop and it said 
"(xfdesktop:4501): Gtk-WARNING **: cannot open display:"
so that means there is something wrong with it right?  Is there a command to reinstall it?  Or will I have to reinstall xubuntu all over again?

Now burning Xubuntu 6.10 to CD to get ready for reinstall if no one knows how to fix... :(

---

### Post by ajgreeny on 2006-11-20
From the terminal, (Ctrl+Alt+F1) login and then try:-
sudo apt-get install xubuntu-desktop
That might just sort out whatever the problem is.  If not, then your complete reinstall may be the only answer.

---

### Post by BliND123 on 2006-11-20
That didn't fix it...Re installation started... :P Hope its done before it gets too late (took like 5 hours last time, didn't seem to install the actual desktop during the first 3 hours then had to do something like that command you said) :P.

---

### Post by BliND123 on 2006-11-20
Hey, what could be wrong with my copy of xubuntu 6.10 alternative?  I did the MD5 checksum thing and it looks ok, but at like 55% or so, I get an error, corrupt file or something.  I burned it at like 1X as I had to for ubuntu 6.06 (which worked, and currently installing this instead to put xubuntu over it) to get it to work, but thats not working for xubuntu, and I am re downloading it right now.

---

