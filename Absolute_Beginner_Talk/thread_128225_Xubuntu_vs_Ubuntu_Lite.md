---
title: "Xubuntu vs Ubuntu Lite"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by johnraff on 2006-02-11
I've seen plenty of posts on Xubuntu and quite a few on Ubuntu Lite, but wondered if anyone had tried both and could compare them?

(I'd really like to use Ubuntu with Gnome but I don't think my 128MB/450MHz machine's up to it)

---

### Post by alfonz on 2006-02-11
Gnome might be really slugish running on that set-up. You are better off with xubuntu which runs with xFce, its light and fast and less bloated so to speak.

---

### Post by majikstreet on 2006-02-11
xfce could be slow on 128mb. it was slow on 256mb for me...

try [https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28low%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28low%29)

and maybe [https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

---

### Post by taurus on 2006-02-11
With your specs, go with fluxbox window manager...  ;)

---

### Post by az on 2006-02-11
Icewm is every bit as fast as fluxbox.

450 Mhz what?  If ti is a pentium, you are good fro the standard install.  If it is a k-6 or a celeron with no cache, then even Xfce is slow.

128 megs if enough for anything.  You can run Gnome or kde with that much and not notice unless you had two or three memory-hogs running at the same time.

---

### Post by dcast on 2006-02-12
I used ubuntu with gnome on my p3 550 with 256 I now use ubuntu lite and it is speedy and great if you have a smaller hard drive and you want to conserve space

---

### Post by David Corrales on 2006-02-12
I agree with the fact that you don't need Fluxbox (yuck). You can still use something Xfce but I really recommend that you get some more ram. Even an old 256mb stick will be a great upgrade :)

---

### Post by johnraff on 2006-02-13
Yea I really just wanted to put in a bit more ram, but by my luck the memory in this box is a bit special (EEC or something) and a 256MB stick would cost $200 or so. :(
I could buy a second-hand box for less than that.

Luckily the cpu is a pentium3 so even 450MHz isn't too awful.

Anyway, Xubuntu runs OK (even Gnome runs, but it *is* slow), but I was wondering how Ubuntu Lite compared.
(that uses Icewm I think)

Fluxbox (or Icewm) and build up from scratch would be another option I guess.

---

### Post by fuscia on 2006-02-13
i've got a 700mhz celeron with 256. i've found that openbox, flwm, 9wm, wmaker, icewm, aewm++ and a few others, all work faster than xfce. they all seem to be about the same speed, so it's more the rest of their qualities that have been important to me (themes, focus, workspaces, etc.).

---

### Post by PhoenixP3K on 2006-03-20
Hi everyone, I've installed Ubuntu 5.10 on my old PC: ( PII 266Mhz, 192 MB RAM, 3 GB HDD, 8 MB video card ) Now that's are good old PC, I failed being able to install Ubuntu Lite directly from the install cd they made so I figured I'd just install Breezy and then change the settings for a "faster" desktop like xfce.

So from what I read on the wiki all I have to do would be
```

sudo apt-get uninstall ubuntu-desktop
sudo apt-get install xubuntu-desktop
```

That last command is supposed to be used when you did a server install but that is _not_ what I did. So I'm scared it's going to take 4 hours to install like it did for the default install.

So I'd be glad if someone would have an opinion on how "faster" Xfce is then Gnome and what are the main consequences of changing the desktop? I mean do a lot of programs change? Settings, are they saved?

---

### Post by johnraff on 2006-03-22
All this is on an "as far as I know" basis, so someone more knowlegable might correct me...
[QUOTE=PhoenixP3K]I failed being able to install Ubuntu Lite directly from the install cd they made[/quote]You could try the method on this thread- direct from the net, and supposed to work better than the cd:
[http://ubuntuforums.org/showthread.php?t=98233](http://ubuntuforums.org/showthread.php?t=98233)
> I figured I'd just install Breezy and then change the settings for a "faster" desktop like xfce.
```

sudo apt-get uninstall ubuntu-desktop
sudo apt-get install xubuntu-desktop
```
I don't think "sudo apt-get uninstall ubuntu-desktop" will do very much. afaik you'll still have all the Gnome stuff on your machine. If you've got plenty of hard disk space that needn't matter too much, in fact if you just want to try out other window managers it's probably better to leave it all there so you can compare them. When you login you should be able to choose xubuntu or gnome, so why not just install xubuntu and see how it goes? I don't think it should take any longer than over a server install.
> So I'd be glad if someone would have an opinion on how "faster" Xfce is then Gnome and what are the main consequences of changing the desktop? I mean do a lot of programs change? Settings, are they saved?Everyone has their own opinions (that's why I started this thread, to hear some... :) ) but xfce does seem to be faster than Gnome. Icewm, which Ubuntu-lite uses, is even faster, but perhaps not as nice... All your programs will still be there, but it might be harder to find them in the menu without some tweaking, and they might look different with a different window manager.

---

### Post by dbmayur on 2007-10-24
I just used the following code:
sudo apt-get install xubuntu-desktop

and after a reboot, I selected Xubuntu from the sessions....make it default, if required...and now my system is really fast!

---

