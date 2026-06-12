---
title: "Cant Bring Window Border Back!!"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by matther22 on 2008-01-07
I just got Ubuntu lst night and installed compiz and was messing with all the cool settings and my window borders dissapeared! I've tried everything i've read in these forums someone please help me!

:confused::confused::confused:

---

### Post by RomeReactor on 2008-01-07
Hi. Open a treminal (Applciations->Accessories->Terminal) and run:
```
gtk-window-decorator --replace
```
and see if you get the borders back.

---

### Post by matther22 on 2008-01-08
Will that work with all the effects activate in compiz?

---

### Post by nero_86 on 2008-01-08
In theory yes.
If it doesn't work you can try to return to metacity whit

```
metacity --replace
```

This will shut down your compiz.

---

### Post by sonofabics on 2008-01-08
> **matther22 said:**
> I just got Ubuntu lst night and installed compiz and was messing with all the cool settings and my window borders dissapeared! I've tried everything i've read in these forums someone please help me!

:confused::confused::confused:

Did you install the compfiz-configurator?
I played with it myself and got the borders removed by one of the options in the compiz configurator.
Unfortunatelly i am at work now where i can't use my ubuntu as it is not the corporate OS :roll:

I belive if you reset to default settings it should bring it back and you can quickly set other effects back.
I removed compiz,alltough it has stunning stuff and can cause vista users to drop their jaws:D but it's not very stable yet and can slow down the pc or even crash. I'll wait for the more stable versions.

---

### Post by bumanie on 2008-01-08
The first thing I would try is to disable compiz and see if that restores the windows. 
When you open terminal, is it just a blank square?
What type of graphics card are you using?

---

### Post by matther22 on 2008-01-08
When i disable compiz my windows return and also i tried the first recomdation and when i closed the terminal after having enter the code (and getting my window borders back)the window borders disappeard again

Im running the ATI Radeon Express 200

---

### Post by RomeReactor on 2008-01-08
> **matther22 said:**
> When i disable compiz my windows return and also i tried the first recomdation and when i closed the terminal after having enter the code (and getting my window borders back)the window borders disappeard again

Im running the ATI Radeon Express 200

First you need to install CompizConfig-Settings-Manager:
```
sudo apt-get install compizconfig-settings-manager
```
Once it's installed, you'll find it in 'System->Preferences->Advanced Desktop Effects Settings'. Open it, go to 'Window Decoration' (make sure it's enabled) and on the "Command" section, write:
```
gtk-window-decorator --replace
```

---

### Post by matther22 on 2008-01-08
Thanks alot for all your guys help but i just completley reinstalled Ubuntu on the drive and if some one could tell me the best  way to install Compiz without it wigging out taht would be great!

---

### Post by RomeReactor on 2008-01-08
What version of Ubuntu did you install: 7.10 (the newest), or a previous one? in 7.10, Compiz is installed by default; to enable it, go to 'System->Preferences->Appearance' and on the last tab ('Visual Effects') select the level of effects you want--I recommend you start with "Normal". If you want to enable or disable individual plugins you just need to install CompizConfig-Settings-Manager.

As a side note, if you have display problems it's not necessary to reinstall Ubuntu; the system is flexible enough that it allows you to solve the problem.

---

### Post by Lostincyberspace on 2008-01-08
> **RomeReactor said:**
> First you need to install CompizConfig-Settings-Manager:
```
sudo apt-get install compizconfig-settings-manager
```
Once it's installed, you'll find it in 'System->Preferences->Advanced Desktop Effects Settings'. Open it, go to 'Window Decoration' (make sure it's enabled) and on the "Command" section, write:
```
gtk-window-decorator --replace
```
Or you could just recheck the window decorations there since that was probably the problem.

---

