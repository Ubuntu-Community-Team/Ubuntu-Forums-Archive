---
title: "Compiz - installed but no info on where it is and"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-30
Hi,

Compiz - installed but no info on where it is and how to actually start it.

Thanks.

---

### Post by JoshHendo on 2006-06-30
What guide did you use to install it?

There is a guide on the forum that will guide you through the installation and set up a small script to start it.

[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

- Josh

---

### Post by u.b.u.n.t.u on 2006-06-30
Those instructions have ruined my ubuntu install.

I lost my gui and had to use vim to edit xorg.conf. I now have a gui but something isn't right. There are a lot of graphical errors.

I am giving up on Compiz. It is too much to ask people to edit this file and that file and make a script and used terminal commands just to install a piece of software to use it.

It is too much on other occasions to expect people to compile software just to use it.

I now need to reinstall ubuntu. Trying to get Compiz to work has completely ruined it for me.

Thanks anyway.

---

### Post by u.b.u.n.t.u on 2006-06-30
Anyone thinking of installing Compiz, think twice. I have just had to reinstall ubuntu. There is no simple install and use. It is complex and wrecked my installation.

---

### Post by someusernoob on 2006-06-30
Im sorry to hear that you had problems with it. The guides spread around the i-net are all pretty good.

Any idea where it went wrong? And what graphics card do you use?

---

### Post by ~LoKe on 2006-06-30
The guides are all pretty clear and elaborated in the case of an error.  You shouldn't have had to reinstall unless you skipped/screwed up on a step, or used a bad guide.

---

### Post by uzi09 on 2006-06-30
well, you were warned it was still in the alpha stages--if not, you didn't have a very good guide :P.

it really depends on how you have it setup, some guides teach you how to set it up so that it's only on one account. others have it on all accounts.

if it's on all accounts, and it's disabled to automatically start up, run:
```
compiz-start
```
to run it from the terminal.
you should get a lil red box with a - and X on it. right click on it to set properties and stuff, otherwise, see if it works by holding CTRL+ALT and left click anywhere on the screen and try to move the lil cube.
other commands you may want to try:
ctrl+alt+left/right will switch desktops
ctrl+alt+shift+left/right will have an app move to different desktops
others...you'll have to hunt around for -- sorry, dunno em all myself.

---

### Post by catlett on 2006-06-30
You are right to be angry. I just checked the how to and the originator of the post left out 2 spots where he should of had you cp a backup. This is really irresponsible on the guide creator.
FYI Because it doesn't matter but he should of had you run this command ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` Right before instructing you to use this command ```
sudo gedit /etc/X11/xorg.conf
``` As well as have you issue this command ```
sudo cp /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom_backup
``` before instructing you to issue this command```
 sudo gedit /etc/gdm/gdm.conf-custom
```
If he had just used those to commands to make backups of those files then all you would of had to do was boot into recovery mode and issue these 2 commands from the command line ```
sudo cp /etc/gdm/gdm.conf-custom_backup /etc/gdm/gdm.conf-custom
``````
sudo cp /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf
```

---

### Post by joshrobinson on 2006-06-30
the editing the gdm.conf files is what screwed my computer over too.. that guide you linked should have had some warnings or restore commands.. but i made note of what files i was editing and went back and fixed them with nano.. since then i have xgl and compiz running, but i select to run xgl/compiz from the login window.. so that way if compiz ever did go wrong, all i have to do is click gnome from the sessions menu and whatever the problem is doesnt screw up my computer

---

### Post by uzi09 on 2006-06-30
you may also want to take a look at the ultimate xgl thread:
[http://ubuntuforums.org/showthread.php?t=148351&highlight=compiz+xgl+aiglx](http://ubuntuforums.org/showthread.php?t=148351&highlight=compiz+xgl+aiglx)

---

