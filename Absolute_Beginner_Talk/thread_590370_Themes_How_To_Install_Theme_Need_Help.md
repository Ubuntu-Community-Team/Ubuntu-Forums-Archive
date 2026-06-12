---
title: "Themes How To Install Theme Need Help"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by MakotoShishio on 2007-10-24
hi,
i have just downloaded and successfully installed Ubuntu 7.10 and i'm loving it.
This is the first time ever using any linux distro.
i have some themes i want to install but i dont know where to start please can some help me. i'm an absolute baby to this.

---

### Post by MegaJim on 2007-10-24
If you have a theme file for Gnome (in .tar.gz format) just drag it into the themes window (system -> preferences -> appearance).

---

### Post by NilsE on 2007-10-24
OR if that does not work extract it to /usr/share/themes with the create folders option active

---

### Post by MakotoShishio on 2007-10-24
i have tried dragging it into system -> preferences -> appearance but it says invalid file format. 
i also tried extracting it into the usr/shar/themes and it says i dont have permission but i'm the only user on the machines??
please help.

---

### Post by NilsE on 2007-10-24
in a terminal do a 

gksudo nautilus

Enter your login password when prompted

then navigate to your archive and it will then let you extract it to /ur/share/themes

---

### Post by MakotoShishio on 2007-10-24
right that is done but how do i select it. i tried going to system > preferences > appearance but i cant find the themes anywhere. by the way all the hlp is very much appricated.

---

### Post by cannontrodder on 2007-10-24
If it says you do not have permission, then good! :)

To achieve the same as NilsE says from the command line, do this:

Your normal user account will not have permissions to do what you are trying which is a good thing as you would not want to accidentally change files in any of those folders. You will need to 'sudo' to root to be able to do it.

So download the theme somewhere in your home directory. Supposing it is called mynewtheme.tgz:

```
tar xvf mynewtheme.tgz
```

...to extract it. You'll then end up with a folder called mynewtheme (obviously depending on the initial package name)

Then you can move this entire folder to where it needs to be:

```
sudo mv mynewtheme /usr/share/themes
```

**sudo** runs commands as super-user (root) but only after you give it your password. The gksudo command NilsE recommended gives you super-user powers as a desktop user.

That should do it?

---

### Post by MakotoShishio on 2007-10-24
i have moved it into the folder but i cant find where to select. i tried system > preference > appearance but i only the the default themes there. help pls.

---

### Post by xtrm_redbull on 2007-10-24
Go to the folder with your name on it, and create a new folder ' .themes ' just copy and paste  the extracted theme folder to it. :)

---

### Post by MakotoShishio on 2007-10-24
thank you for your time i managed with all your help to get working. thanks a bunch.

---

### Post by NilsE on 2007-10-24
> **MakotoShishio said:**
> thank you for your time i managed with all your help to get working. thanks a bunch.
Just so you know for the future, most themes don't show up in appearance/themes as complete themes.  Most are just a piece of a theme (window frames, controls, etc)  that can be selected with the customize option on the theme tab.

When you copy a theme to your home folder .themes you just make it think it is a theme but it is still a piece that you can modify with the theme/customize option.

---

