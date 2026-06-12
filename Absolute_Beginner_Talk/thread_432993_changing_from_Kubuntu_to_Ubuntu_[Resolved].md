---
title: "changing from Kubuntu to Ubuntu [Resolved]"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by JerryAtrik on 2007-05-04
I have been trying out Kubuntu for the last week or so because I thought it looked an easier system but it does not seem to have as much in the way of programs than the copy of Ubuntu that I have .Is it best to do a clean install or are there any snugs .?? .
cheers JerryAtrik.:confused:

---

### Post by jfinkels on 2007-05-04
> **JerryAtrik said:**
> I have been trying out Kubuntu for the last week or so because I thought it looked an easier system but it does not seem to have as much in the way of programs than the copy of Ubuntu that I have .Is it best to do a clean install or are there any snugs .?? .
cheers JerryAtrik.:confused:

I don't know what a "snug" is, but you can do this:
```

sudo aptitude remove kubuntu-desktop && sudo aptitude install ubuntu-desktop

```

---

### Post by starcraft.man on 2007-05-04
> **jfinkels said:**
> I don't know what a "snug" is, but you can do this:


He means snag :) (I don't know how you typo a u for an a though :p)

---

### Post by aysiu on 2007-05-04
I don't know if ```
sudo aptitude remove kubuntu-desktop
``` is going to do anything unless Kubuntu was originally installed with ```
sudo aptitude install kubuntu-desktop
```

Try these instructions:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

And then these if you really hate KDE:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by NICU on 2007-05-04
Hey before you go uninstalling everything - you can have both KDE and Gnome (Kubuntu and Ubuntu) on the same PC.  You can install the Ubuntu (Gnome) desktop with ```
sudo apt-get install ubuntu-desktop
``` Once that installs, at the sign-in screen you can choose Options or Sessions and change your session between KDE and Gnome.  After you try them both out for a while you can remove the applications and anything else you don't want.

---

### Post by JerryAtrik on 2007-05-05
Cheers folks will see what I can do. Will  let you know how it goes

---

### Post by JerryAtrik on 2007-05-06
Cheers folks I am all up and running
regarding snug for snag considering where the keys are I don`t know how I did it.

---

### Post by starcraft.man on 2007-05-06
> **JerryAtrik said:**
> Cheers folks I am all up and running
regarding snug for snag considering where the keys are I don`t know how I did it.

Well, glad to have you aboard jerry. Don't worry, there are no grammar/spelling police on these forums.... yet :p

---

