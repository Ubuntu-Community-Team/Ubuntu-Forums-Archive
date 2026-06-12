---
title: "Replace default apps with different apps?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Bwangster12 on 2007-07-31
I have installed a command line system using XFCE and some other simple stuff.  For some reason Thunar seems to have installed automatically.  Is there a way I can safely uninstall that and use something like PCMan instead?  I have heard that PCMan is lighter on system resources and that is what I am looking for.

Similarly.... I was contemplating installing something like Epiphany because Firefox seems to be a monster when I am using it.  Everything appears to run pretty slowly when it is open.  Only thing is when I try to install Epiphany it seems like Firefox gets installed to.

What are some good default program replacements to help lighten my laptop?

---

### Post by wolfen69 on 2007-07-31
```
sudo aptitude update
```
```
sudo aptitude remove thunar
```

---

### Post by Bwangster12 on 2007-07-31
Doing this will just remove Thunar?  

I don't understand the whole situation that occurs when I try to uninstall something and it tells me that it also needs to remove XFCE or Xubuntu-Desktop... or so on.

---

### Post by kerry_s on 2007-07-31
thunar is part of xfce4, you can not remove it and still keep xfce4. thunar is lighter than pcmanfm, it is also more mature & stable compared to pcmanfm. pcmanfm is buggy as hell.

if you want to, select every little application, you should use a WM like icewm,fluxbox, etc... they are truly light, with nothing but what you add, xfce4 is considered a medium DE, that is on it's way to bloat hell, all pieces are getting to tied together so when 1 part fails, it takes everything else down with it & kicks you out to login.

---

### Post by Ek0nomik on 2007-07-31
> **kerry_s said:**
> thunar is part of xfce4, you can not remove it and still keep xfce4. thunar is lighter than pcmanfm, it is also more mature & stable compared to pcmanfm. pcmanfm is buggy as hell.

if you want to, select every little application, you should use a WM like icewm,fluxbox, etc... they are truly light, with nothing but what you add, xfce4 is considered a medium DE, that is on it's way to bloat hell, all pieces are getting to tied together so when 1 part fails, it takes everything else down with it & kicks you out to login.

Can you provide more reading on this kerry_s?  I am curious to know more about how environments handle this situation.  Or is there a more specific name for this that I can look it up myself.

---

### Post by RedSquirrel on 2007-07-31
> **Bwangster12 said:**
> What are some good default program replacements to help lighten my laptop?

Have a look at this thread:

[Lightweight apps]("http://ubuntuforums.org/showthread.php?t=447007")

---

### Post by kerry_s on 2007-07-31
What i recommend is do the command line install.then

sudo apt-get install xorg gdm synaptic icewm menu rox-filer leafpad
reboot(ctrl+alt+delete)
select icewm in session and log in
open synaptic and get what ever else you want.

there are programs to help you with changing menus and toolbars, i'll leave that choice up to you, i just use "icemc" and do everything else with a text editor. use rox for the desktop if you want desktop icons.

here's the guide> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

What are your specs?

i use a similar setup on a 450mhz 256ram laptop and it's fast. i use mcedit for my editor and my toolbars on autohide, my menus trim, i mainly use the win key+spacebar to call the toolbar launcher and just type the app name.

---

