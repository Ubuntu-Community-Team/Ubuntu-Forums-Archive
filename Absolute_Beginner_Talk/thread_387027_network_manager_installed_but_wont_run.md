---
title: "network manager installed but wont run"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by atd85 on 2007-03-17
i've installed network-manager via the add/remove option under applications and it said it installed fine but the icon never showed up.  so i removed it via add/remove, still no luck, so then i used apt-get and typed..   sudo apt-get install network-manager-gnome and it said it installed, but it still doesnt show up.. when i try to run it from the command line i type sudo NetworkManager as i read on the forums.. and when i type ps -A it shows it running.. but nothing happens, i dont see any kind of interface.. i'm stumped.. please help

---

### Post by cbudden on 2007-03-17
When you install network manager, it usually installed a entry for your startup programs.  The command to run it is nm-applet --sm-disable
If you run that from the command line, or Alt-F2 you should get the icon appear in the notification area.
To see if it is in your startup programs, go to System - Preferences - Sessions, and click the third tab along, and look for nm-applet --sm-disable in there.  If it is not, then add it.

If it does appear, but you cannot connect to a wireless network/wired network because nothing shows up, it is probably due to your /etc/network/interfaces file having existing configuration information in it.  Open a terminal, type 
```

gksudo gedit /etc/network/interfaces

```
and remove any references to interfaces that are not the "lo" interface.
My file looks like this:

auto lo
iface lo inet loopback

---

### Post by atd85 on 2007-03-17
well i got it to work.. kinda a stupid problem.. when i was messing with my panels i somehow deleted the notification area entirely.. although when i did find out that was the problem, i still had to type in the command you gave me.. and also for future reference.. why didnt it add it to my applicaiton menu? and where was it installed at? and is there an icon for it so i can add it manually (i know i'm picky)

more importantly though.. now that i got it running.. it wont connect to my network.. it finds it, but it'll just say "attempting to join" and eventually time out.. i know my network is working because if i go back to system>administration>networking and enable it through there it'll work.. i opened my /etc/network/interfaces file and deleted everything except for the sample line you posted.. so close, its almost there.. thanks again

---

### Post by atd85 on 2007-03-18
well it seemed to magically fix itself after a restart.. thanks for the help!

---

