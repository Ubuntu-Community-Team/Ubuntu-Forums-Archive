---
title: "Need help with Adept and KMenu"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Zeikcied on 2006-10-25
I have installed several programs, most of them games, via Adept (using Kubuntu, obviously), and they haven't shown up in the KMenu.

Most of the programs I have installed have made entries in the KMenu, but the games have not.  I can't keep track of the names of them all, so I don't know how I'm going to launch them without shortcuts.

How can I make them show up?  What am I missing here?  Do I need to restart X and KDE?

---

### Post by OptimusPrime on 2006-10-25
I use Gnome, but I bet there is a menu editor in your apps toolbar, you should be able to turn on those games so you can see them from the game menu. Do you have one?  Mine is the Alacarte menu editor.

---

### Post by d3v1ant_0n3 on 2006-10-25
I've found that some programs don't show up in the Kmenu until after a reboot, and some not at all-especially if you don't have the 'debian' programs entry in Kmenu. I assume there's a way of refreshing the menu entries, but I just deal with it via rebooting- I shut down the comp when I;m not using it anyway, so it's not a hassle for me.

Sorry that's not more help.

*edit* for a menu editor for Kmenu, right click on the Kmenu icon (you might have to unlock panels first if they're locked) and select 'menu editor'

---

### Post by OptimusPrime on 2006-10-25
Just look for a menu editor, it's in your Apps.  I was having the same problems.

---

### Post by Jucato on 2006-10-25
@d3v1ant_0n3: this command is all you need to refresh K Menu manually:
```
kbuildsycoca --incremental
```
At most, you don't need to completely reboot. A quick logout will do. This seems to have been fixed in Edgy. New programs appear instantly

@OptimusPrime: the KDE Menu Editor (kmenuedit) isn't in the menus, by default. You either have to type it in (Alt+F2), or right-click the menu.

@Zeikceid: usually, new apps are added immediately to the K Menu. if not, use the command I gave earlier. If the game still does not appear in K Menu, then it means that the game wasn't meant to be started from the K Menu, or that it's missing the proper configuration that will put it in K Menu. either way, you can try exploring in /usr/bin or /usr for the name of the game.

---

### Post by OptimusPrime on 2006-10-25
> **Jucato said:**
> @d3v1ant_0n3: this command is all you need to refresh K Menu manually:
```
kbuildsycoca --incremental
```
At most, you don't need to completely reboot. A quick logout will do. This seems to have been fixed in Edgy. New programs appear instantly

@OptimusPrime: the KDE Menu Editor (kmenuedit) isn't in the menus, by default. You either have to type it in (Alt+F2), or right-click the menu.

@Zeikceid: usually, new apps are added immediately to the K Menu. if not, use the command I gave earlier. If the game still does not appear in K Menu, then it means that the game wasn't meant to be started from the K Menu, or that it's missing the proper configuration that will put it in K Menu. either way, you can try exploring in /usr/bin or /usr for the name of the game.

Oh, sorry.  I have never used KDE.  I wish I could have both on here.

---

### Post by Zeikcied on 2006-10-26
> **Jucato said:**
> @d3v1ant_0n3: this command is all you need to refresh K Menu manually:
```
kbuildsycoca --incremental
```
At most, you don't need to completely reboot. A quick logout will do. This seems to have been fixed in Edgy. New programs appear instantly

@OptimusPrime: the KDE Menu Editor (kmenuedit) isn't in the menus, by default. You either have to type it in (Alt+F2), or right-click the menu.

@Zeikceid: usually, new apps are added immediately to the K Menu. if not, use the command I gave earlier. If the game still does not appear in K Menu, then it means that the game wasn't meant to be started from the K Menu, or that it's missing the proper configuration that will put it in K Menu. either way, you can try exploring in /usr/bin or /usr for the name of the game.

That command worked.  Thanks a lot! :D

---

### Post by msak007 on 2006-11-19
So what do you do if you issue a 
```
 kbuildsycoca --incremental
```
And get the error 

```
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
```After which KMenu entries that are missing still don't show up. And a restart didn't help either. This is on a new Edgy install using the same /home directory that I backed up / restored from a Dapper install.

---

### Post by Jucato on 2006-11-19
Those error messages are normal, as far as I know.

What app did you install that is not being added to the K Menu. Like I said earlier, some apps really do not get added to the K Menu at all. Some examples are 3D Chess, Wine itself (some apps installed by Wine do get added, though), htmldoc, and command line apps/utilities like GCC.

---

### Post by msak007 on 2006-11-19
I've been around for a while, so I know which apps don't show up in the menus :). But FireStarter isn't one of those apps, unless it's some bug in Edgy. I uninstalled and reinstalled it and it still didn't show up. I had to edit the menu and add it manually.

---

### Post by ewl1217 on 2006-11-19
Not all programs have menu entries compatible with Ubuntu (including Kubuntu and Xubuntu). For those programs, you'll need to install the Debian menu. Just run this:
```
sudo apt-get install menu
```
You should see a Debian entry in KMenu. Look for your programs in there.

---

### Post by Jucato on 2006-11-20
> **msak007 said:**
> I've been around for a while, so I know which apps don't show up in the menus :). But FireStarter isn't one of those apps, unless it's some bug in Edgy. I uninstalled and reinstalled it and it still didn't show up. I had to edit the menu and add it manually.

I just installed firestarter to test. It was automatically added to K Menu -> System. So I'm not sure what's happening on your computer to make it not add the item in your K Menu.

---

### Post by msak007 on 2006-11-20
> **Jucato said:**
> I just installed firestarter to test. It was automatically added to K Menu -> System. So I'm not sure what's happening on your computer to make it not add the item in your K Menu.I assumed something was wrong with my setup, which is why I was asking for help. I know it normally ends up in System but I couldn't find it. I poked around a little and ended up deleting **~/.config/menus/applications-kmenuedit.menu** and then running kbuildsycoca. This brought Firestarter back, but also brought some empty entries from apps I had installed in my previous Dapper install. It put most of them in "Lost & Found", and these are entries which I deleted as soon as I booted Edgy. Now all I need to do is find out where those settings are stored and "reset" the kmenu back to default, to only show apps that are currently installed.

Edit: I figured it out. I also had to delete the contents of **~/.local/share/applications** and **~/.local/share/desktop-directories**. Just for good measure I ran kbuildsycoca --incremental after I did that, and it reset the KMenu back to the default and any customizations / left over programs were gone. At least I learned something in the process. :)

---

