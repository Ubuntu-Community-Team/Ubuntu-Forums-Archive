---
title: "Error MSG"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-01
Hi I have been running ubuntu for a few days now and now after I boot up I get this msg as ubuntu is loading Cannot open theme file/usr/share/apps/kdm/themes/kubuntu , (yes that says kubuntu), so I have no idea how to get rid of this please help

---

### Post by DaveNF2G on 2006-10-20
I get the same message.  It happens before the login screen comes up.

---

### Post by aysiu on 2006-10-20
Did you go to /usr/share/apps/kdm/themes and see if a kubuntu folder is there?

Are you using KDM?

Are you in Edgy or Dapper?

---

### Post by ReaderRat on 2006-10-20
Try:
Graphics (Repair)
          ```
sudo dpkg-reconfigure xserver-xorg
```

This works in Ubuntu sometimes.

EDIT: Nevermind, **[color=RED]aysiu[/color]** is here. You're in good hands....

---

### Post by jordanmthomas on 2006-10-20
This error means that 
a) you are running kubuntu and using kdm instead of gdm
and
b) You no longer have the default kdm theme installed.

You have a few options.
**option 1**
you can change back to gdm instead.
```
sudo nano /etc/X11/default-display-manager
```
Change it from
```
/usr/bin/kdm
```
to
```
/usr/**s**bin/**g**dm
```

It shouldn't bother you after that.

**option 2**
reinstall default kdm theme
```
sudo aptitude reinstall kubuntu-default-settings
```

**option 3**
continue using kdm and choose a new theme
```
sudo aptitude install kcontrol-kdmtheme kde-kdm-themes
```
Then, run kcontrol and find the KDM theme section and select one.

...that's all I can think of now.  Hopefully at least one of these will work for you.  :)

---

### Post by DaveNF2G on 2006-10-21
In response to aysiu and the others, here are more details.

I am running Edgy Eft.

I normally run GDM, but KDM is installed and the login screen, where I have the option to select a subtype of Ubuntu, says "Welcome to Kubuntu" at the top.  However, the error message appears **before** the login screen does.

There is no /kubuntu folder in .../themes.

I have run the KDE desktop under the current install.  

Should I just boot to KDE and install a theme there?

EDIT: Ok, I tried booting to KDE and installing a theme, then restarting.  No change in behavior - the error message still appears.

---

### Post by aysiu on 2006-10-21
If you're running Edgy Eft, it could be a bug, and you should report it.
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

