---
title: "can't boot gutsy gui after kde 4.0 disaster"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by maya9 on 2008-01-13
[I posted this on another area of the forum...sorry for the cross post but I'm not sure where I ought to go...and I'm desperate for help!]

Having a terrible time. Mayday!

Installed KDE 4 last night on top of Gutsy. When it came time to start things up, I got a half screen of snow, then a blue screen with an off center box saying "Welcome to Debian" and a log in. I tried logging in using every option (gnome, kde, kde 4.0) and it always took me to a flat blue screen with a terminal window.

So I restart in recovery mode to a command line, do sudo gdm, and get a ubuntu login screen with system options. I try the kde 4.0 and it runs, though VERY buggy. At this point I just want to get it OFF my system and get back to my lovely gutsy. Restart in similar manner and choose gnome and things are good (except I can't go online).

I then try various remove strategies,
sudo aptitude remove kubuntu-desktop
sudo apt-get remove kubuntu-desktop
going into synaptic and searching for kde files

Sorry, I don't know enough to know what I'm doing.
Anyway, restarting now takes me past the grub screen and then to a half screen of stripy zig-zag lines and then a BLANK BLACK screen and then nothing more. Just black. I have to hold the button down to get it to turn off.

I can still reboot in recovery mode as I did before and it appears that KDE is gone--it isn't showing up in the login screen's options. What happened? How do I get a normal start up into gutsy?

KDE looked really cool and sexy but it did NOT work at all on my system.

Thanks!

---

### Post by Toxicity999 on 2008-01-13
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure gdm
Choose gdm, then you will use GDM by default, this should fix a lot of your issues.

---

