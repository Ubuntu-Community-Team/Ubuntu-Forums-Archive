---
title: "System restore or problem fix?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Aaron_Griffiths_92 on 2008-03-10
I was playing around with my desktop cube, changing the top pictures and so on, but then it crashed completely, all my desktop effects are broken etc, is there any system restore program i can use to get back my original interface?

---

### Post by elpichi on 2008-03-10
if you want a complete restore of the settings you can always purge the application you are running for the effects.
But If all you want is to make it work again, i say a quick log off/restart should make it work unless is a very persistent error >.>.

to Purge the application, you can use the terminal and type:
sudo apt-get purge <name of the application>
and then to reinstall it back
sudo apt-get install <name of the application>


i'm pretty sure there are other ways to do it, but this should be the easiest/fastest.

---

### Post by Aaron_Griffiths_92 on 2008-03-10
problem... no idea what the app is called, its just advanced effects, i want to restore my WHOLE system, cairo clock has been damaged, so has my whole interface, i just need to start again without re formatting my HDD as i have a dual boot.

---

### Post by jordanmthomas on 2008-03-10
```
rm -r ~/.config/compiz
```
Will reset compiz to its defaults and you should be able to run it again.

EDIT:
Nevermind, you just said you want to reinstall everything.

If you have a dual boot, it will still work if you reinstall Ubuntu into the same partitions.

---

### Post by Aaron_Griffiths_92 on 2008-03-10
and how do i do that?

---

### Post by elpichi on 2008-03-10
in that case you can
use this command in the terminal 
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity

note: when you try to log in change the session to terminal only, this will allow you to type the command

---

### Post by Aaron_Griffiths_92 on 2008-03-10
what did i just do using that command?

---

### Post by elpichi on 2008-03-10
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity
That removes any current settings that you have with those programs(gnome/gnome2/gconf/gconfd/metacity) and makes all the settings default.(These files control the visual settings of your desktop)

---

### Post by forrestcupp on 2008-03-11
> **elpichi said:**
> if you want a complete restore of the settings you can always purge the application you are running for the effects.
But If all you want is to make it work again, i say a quick log off/restart should make it work unless is a very persistent error >.>.

to Purge the application, you can use the terminal and type:
sudo apt-get purge <name of the application>
and then to reinstall it back
sudo apt-get install <name of the application>


i'm pretty sure there are other ways to do it, but this should be the easiest/fastest.

> **Aaron_Griffiths_92 said:**
> problem... no idea what the app is called, its just advanced effects, i want to restore my WHOLE system, cairo clock has been damaged, so has my whole interface, i just need to start again without re formatting my HDD as i have a dual boot.

Try
```
sudo apt-get --purge remove compiz compizconfig-settings-manager
```
to remove Compiz and its settings, which is the name of the visual effects.  Those are the names you were looking for.  

Then reinstall it:
```
sudo apt-get install compiz compizconfig-settings-manager
```
Hopefully that will take care of all of your problems.

We don't have a System Restore like Windows does.  I have suggested something like that in the past, and the main response was that System Restore in Windows doesn't work and it wouldn't be a useful tool.  I disagree on both points.

---

### Post by Cerny on 2008-03-11
In a worst case situation if you can't get some parts restored you may just have to install ubuntu from the live cd. But i can see how that is just time consuming.

---

