---
title: "Point me to a launcher how-to?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by adampyre on 2007-04-21
Hi,

I am looking for a launcher-command how to. It doesn't seem to function as it would typing the commands directly into bash. Specifically, I am trying to create an application launcher that when clicked, opens a terminal session, backs up xorg.conf to a folder called xorgbackup and then nano edits xorg.conf.

Alone, sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.bak works
and sudo nano /etc/X11/xorg.conf works, but how do i combine them so they work in one launcher? so it first backs up then opens xorg.conf?

I tried sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.bak && gedit /etc/X11/xorg.conf

and

udo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.bak; gedit /etc/X11/xorg.conf

niether work. any tips?

Thanks!

---

### Post by maniacmusician on 2007-05-05
> **adampyre said:**
> Hi,

I am looking for a launcher-command how to. It doesn't seem to function as it would typing the commands directly into bash. Specifically, I am trying to create an application launcher that when clicked, opens a terminal session, backs up xorg.conf to a folder called xorgbackup and then nano edits xorg.conf.

Alone, sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.bak works
and sudo nano /etc/X11/xorg.conf works, but how do i combine them so they work in one launcher? so it first backs up then opens xorg.conf?

I tried sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.bak && gedit /etc/X11/xorg.conf

and

udo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.bak; gedit /etc/X11/xorg.conf

niether work. any tips?

Thanks!
I'm not really sure how to do that with launchers...but I know another great way to do it. Bash aliases. [http://ubuntu-tutorials.com/2007/03/30/creating-shortcuts-with-user-aliases/](http://ubuntu-tutorials.com/2007/03/30/creating-shortcuts-with-user-aliases/)

so for your current situation, you might want to add an:
```

alias editxorg='sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.conf.bak && sudo nano /etc/X11/xorg.conf'
```

Actually, that didn't work for me at first either. The reason is that the cp command can't create the xorgbackup directory for  you. so what you need to do is make that directory yourself, and then the launcher should work. Use: sudo mkdir /etc/X11/xorgbackup and then the launcher will work. Personally, I prefer the bash alias way. because then, I can have a command like this:

```
alias restorexorg='sudo cp /etc/X11/xorgbackup/xorg.conf.bak /etc/X11/xorg.conf'
```

which just restores your xorg.conf for you. I have tons of aliases set up already.

---

