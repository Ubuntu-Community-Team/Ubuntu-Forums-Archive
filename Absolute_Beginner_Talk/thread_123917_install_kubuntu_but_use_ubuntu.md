---
title: "install kubuntu but use ubuntu?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by asinsh on 2006-01-31
I apologize for the beginner question but I'm in teh "Absolute Beginner Talk' area, so here goes:

I just installed kubuntu as a dual boot with winXP and everything looks ok so far.  But if I want to go back and forth between kubuntu and ubuntu, do I need to install ubuntu separately and set up a tri-boot with XP, kubuntu and ubuntu?

---

### Post by aysiu on 2006-01-31
Just open a Konsole and type these commands: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` Log out. Click on **Session** and **Gnome** and log back in again.

---

### Post by asinsh on 2006-01-31
[QUOTE=aysiu]Just open a Konsole and type these commands: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` Log out. Click on **Session** and **Gnome** and log back in again.[/QUOTE]

Sounds easy.  Thanks!  Will that put me in exactly the same position I would have been in if I had started with ubuntu and tried to do the same thing with kde?

---

### Post by Stealth on 2006-01-31
Yes. The only thing you may not like about it is the fact that your applications list is now huge, since you got programs from KDE *AND* GNOME...:D

---

### Post by asinsh on 2006-01-31
[QUOTE=Stealth]Yes. The only thing you may not like about it is the fact that your applications list is now huge, since you got programs from KDE *AND* GNOME...:D[/QUOTE]
I've seen a faq somewhere where they show you what the windows equivalent program is in ubuntu and in kubuntu (for example IE => firefox in ubuntu and konqueror in kubuntu).  Do you mean that if I do what you suggest I will end up with each and every app from both (firefox and konqueror)?

That doesn't sound like a bad thing, is it?  I have essentially unlimited HD space so if the only issue is wasted space that's not a big deal.  And I imagine I can always delete duplicate apps if I want, right?

Or are you saying that I will be seriously cluttering up the interface and that I should think twice before doing it this way?

---

### Post by mcduck on 2006-01-31
not seriously, but sure you're menus will be full of programs. But you can remove those you don't need, or use menu editors to remove KDE apps from Gnome menu and Gnome apps from KDE menu if you want.

---

### Post by Sutekh on 2006-01-31
Each program has a .desktop file located in /usr/share/applications and /usr/share/applications/kde

The applications will show up in GNOME and KDE unless you add a line in each and every .desktop file, such as
```
OnlyShowIn=KDE;
```
Fortunately [Xian]("http://www.ubuntuforums.org/member.php?u=37") has got a script to do that for you
[http://www.ubuntuforums.org/showpost.php?p=532770&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=532770&postcount=2")

To go the other way and remove GNOME entries in KDE, slightly modify the code
```
cd /usr/share/applications/
sudo chmod a+rw /usr/share/applications/*
for i in *; do echo "OnlyShowIn=GNOME;" >> $i; done
sudo chmod 644 /usr/share/applications/*
```

---

