---
title: "kubuntu confusion"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-07-27
Is Kubuntu basically Ubuntu, but just uses KDE instead of Gnome? I've been using Ubuntu and just installed the kubuntu desktop to see what it was like. I do kinda like it more however I have run into some slight issues.

1. Firefox and Thunderbird won't start.. if I click on it it'll say it's loading and then it just disappears.
2. Is Wine used in Kubuntu?? Because when I look in the K Menu, my Wine programs show up under Lost and Found?!

Basically I guess I'm asking how is it easiest to migrate from Ubuntu to Kbuntu? Mostly just so I don't have to specify if I want to sign in to use Gnome or KDE. Is there anything I should uninstall so there aren't any conflicts? Thanks!!

Andrea

---

### Post by ev5unleash1 on 2007-07-27
Yea but I think the Ubuntu Team is pointing for future products to use the Gnome environment. Take a look at Ubuntustudio.com for instance.

---

### Post by RomeReactor on 2007-07-27
Hi. Yes Ubuntu and Kubuntu are the same collection of underlying programs, just a different desktop environment. As for Firefox and Thunderbird not starting, I suggest you first run them in Konsole to see if they print any errors; just type either **firefox** or **thunderbird** and press enter. You can also try changing the GTK theme they're using, to see if that solves the problem; to do that you must go to the **Appearance** part of the Control Center (can't remember it's correct name).

Your Wine entries probably appeared in Lost & Found because they are entries you yourself made to the menu; just move them to the menu you want.

---

### Post by aysiu on 2007-07-27
> **andyho said:**
> Is Kubuntu basically Ubuntu, but just uses KDE instead of Gnome? Yes. Different desktop environment, different default programs, and different artwork. Otherwise exactly the same. > I've been using Ubuntu and just installed the kubuntu desktop to see what it was like. I do kinda like it more however I have run into some slight issues.

1. Firefox and Thunderbird won't start.. if I click on it it'll say it's loading and then it just disappears. The best way to diagnose this is through the terminal. To launch a terminal, press Alt-F2 and type ```
konsole
``` Within the Konsole terminal, type ```
firefox
``` If you get any error messages, paste them back here. > 2. Is Wine used in Kubuntu?? Because when I look in the K Menu, my Wine programs show up under Lost and Found?! Wine isn't normally included in Kubuntu, but if you'd installed Wine before, it may have just shown up in the menus. It shows up in mine (even the Gnome menu, but with no icons).

> Basically I guess I'm asking how is it easiest to migrate from Ubuntu to Kbuntu? Just start using Kubuntu, as you've been doing. There's no need to migrate. All your files are in the same place they were before, and you can have both Ubuntu and Kubuntu installed at the same time. > Mostly just so I don't have to specify if I want to sign in to use Gnome or KDE. Is there anything I should uninstall so there aren't any conflicts? Thanks!! If you use KDM as your default display manager, it will automatically remember the last desktop environment you logged in as and not ask you for confirmation when you want to switch. To change from GDM to KDM, log out, press Control-Alt-F1, log in, type: ```
sudo /etc/init.d/gdm stop
sudo apt-get install kdm
sudo nano -B /etc/X11/default-display-manager
``` Change ```
/usr/sbin/gdm
``` to ```
/usr/bin/kdm
``` then save (Control-X, Y, Enter) and finally ```
sudo /etc/init.d/kdm start
```

---

### Post by andyho on 2007-07-27
> **aysiu said:**
> ... launch a terminal, press Alt-F2 and type ```
konsole
``` Within the Konsole terminal, type ```
firefox
``` If you get any error messages, paste them back here.  


Here's what I got...

andyho@andyho-ubuntu:~$ firefox
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)

---

### Post by aysiu on 2007-07-27
Maybe [this](http://ubuntuforums.org/showthread.php?p=1264009) might help?

---

### Post by andyho on 2007-07-27
hmm the only bad thing is I actually do have a wacom tablet I plan on using at times! So if I change the config file, would I have to enable them again? Could it possibly be my vid card settings? I was having the worst time trying to install it; nvidia geforce 5200. Just got it to work yesterday! :lol:

EDIT: ok never mind... tablet PC!! not actual tablet.. I'll try it out!:)

---

### Post by andyho on 2007-07-27
Hmmm well I tried that.. no such luck.. I then went and messed with my vid card and now I'm only getting...

andyho@andyho-ubuntu:~$ firefox
Segmentation fault (core dumped)
andyho@andyho-ubuntu:~$ 

weird?!?

---

### Post by aysiu on 2007-07-27
Can you see if this makes a difference? ```
mv ~/.mozilla ~/.mozilla.backup
firefox &
``` It won't launch with your bookmarks, history, extensions, themes, or passwords, but maybe it will launch.

---

### Post by andyho on 2007-07-27
Here's what I got...

andyho@andyho-ubuntu:~$ mv ~/.mozilla ~/.mozilla.backup
andyho@andyho-ubuntu:~$ firefox &
[1] 5808
andyho@andyho-ubuntu:~$ Segmentation fault (core dumped)


Should I possibly uninstall it and then reinstall it??

---

### Post by aysiu on 2007-07-27
I'm not sure that'd make much of a difference. Well, for now, let's move your old settings back: ```
rm -r ~/.mozilla
mv ~/.mozilla.backup ~/.mozilla
```

---

### Post by andyho on 2007-07-27
ok, did that.. and here's another thing I just noticed.. in my usr/bin I've gotta mozilla-firefox and moziall-firefox.ubuntu files.. same thing for thunderbird. Is that causing a conflict?!

---

