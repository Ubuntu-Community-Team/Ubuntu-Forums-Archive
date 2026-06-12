---
title: "Need to remove GNOME and KDE and reinstall Ubuntu-Desktop on Ubuntu Server"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by jordantbro on 2006-10-03
First I installed Ubuntu Server.  Then I decided to add Gnome.  After a while I added KDE.  Now when I boot it comes to the Kubuntu loading screen and never moves.  The webserver runs (which is what I really need), and I can get to the console with Ctrl-Alt-F1.

That said, I need Gnome back again. I don't really care if I have to lose KDE or not.

Anyone with experience reinstalling Gome?  Help is really appreciated.

Jordan

---

### Post by Rui Pais on 2006-10-03
How do you added gnome and kde? with apt-get(synaptic) or aptitude?

Try:
```
sudo aptitude purge kde-core kdebase kubuntu-desktop
``` 
and then
```
sudo aptitude reinstall ubuntu-desktop
```

Specially with meta-packages is important to install with aptitude, instead of apt-get that have a less good dependency checks.

hope that helps

---

### Post by jordantbro on 2006-10-03
I used apt-get to install, thanks for the tip I will use aptitude from now on.  Will using the commands you suggested cause any problems because I installed using apt-get?

Thanks,

Jordan

---

### Post by az on 2006-10-03
Whether you use one or the other it will not make any difference.

Not knowing exactly what packages you installed, I would guess that your display manager (session manager) is misconfigured.  try

sudo dpkg-reconfigure gdm

and make it default.  Then, when you boot into it, try to pick the gnome session.  If the gnome session is not there, then you removed it and should be able to reinstall it by installing ubuntu-desktop.

---

### Post by jordantbro on 2006-10-03
> **azz said:**
> Whether you use one or the other it will not make any difference.

Not knowing exactly what packages you installed, I would guess that your display manager (session manager) is misconfigured.  try

sudo dpkg-reconfigure gdm

and make it default.  Then, when you boot into it, try to pick the gnome session.  If the gnome session is not there, then you removed it and should be able to reinstall it by installing ubuntu-desktop.

Perfect, I will try this tomorrow when I get to work.

In less than 2 months I went from almost never using Linux... to EdgtEft beta on my home desktop, 6.06 LTS on my laptop and Ubuntu server running the web based bug tracker at work.  It has been a really neat progression.  Thanks everyone.

Jordan

---

### Post by Rui Pais on 2006-10-04
> **azz said:**
> Whether you use one or the other it will not make any difference.

Hi, not exactly. There is a huge difference in case of meta-packages. 
**aptitude remove package** will remove package and any dependency of it (at least it can do it if package was installed via aptitude).
While **apt-get remove package** will only remove the package.

With stuff like gnome, xfce, kde and kind if do, as an example:
```
aptitude install ubuntu-desktop
```
will install Gnome desktop and keep a track of all dependencies.
```
apt-get remove ubuntu-desktop
```
to remove **only** the meta-package ubuntu-desktop, that try to prevents me to delete some stuff i may not want (like evms or others).
Or
```
aptitude remove ubuntu-desktop
```
to get rid of gnome desktop.

Check [here]("http://www.ubuntuforums.org/showthread.php?t=164082") for a deeper discussion on the subject.


> Not knowing exactly what packages you installed, I would guess that your display manager (session manager) is misconfigured.  try

sudo dpkg-reconfigure gdm

and make it default.  Then, when you boot into it, try to pick the gnome session.  If the gnome session is not there, then you removed it and should be able to reinstall it by installing ubuntu-desktop.

You are right of course, thats a broken display manager that can be reconfigured as you said. 
But after solved that problem, configuring correctly gdm, kdm will continue to be installed, not working, and occupying space.
Thats why trying to remove it may deserves a trial ;)

---

### Post by az on 2006-10-04
> **Rui Pais said:**
> Hi, not exactly. There is a huge difference in case of meta-packages. 
**aptitude remove package** will remove package and any dependency of it (at least it can do it if package was installed via aptitude).

That in of itself is irrelevant to most people as well as in this case specifically since the packages were not installed using aptitude.  Bringing up the difference in those two applications only confuses the issue here.

> **Rui Pais said:**
> 
 kdm will continue to be installed, not working, and occupying space.
Thats why trying to remove it may deserves a trial ;)

Again, that does not address the problem.  Removing a bunch of applications is another issue.  KDM will not cause any problems if you run GDM.

---

### Post by Rui Pais on 2006-10-04
> **azz said:**
> That in of itself is irrelevant to most people as well as in this case specifically since the packages were not installed using aptitude.  Bringing up the difference in those two applications only confuses the issue here.

> **azz said:**
> Again, that does not address the problem.  Removing a bunch of applications is another issue.  KDM will not cause any problems if you run GDM.

Although the tone of your post, thats only an opinion, yours. You are absolutely on your right to have it and say it, as i have mine. 
But since jordantbro's thread is titled > Need to remove GNOME and KDE and reinstall Ubuntu-Desktop on Ubuntu Server and those apt/aptitude are the most used to install and remove apps (and i never saw someone who wishes to have useless broken software installed just for fun) i fail to see the redundancy... My problem, probably.

Have a nice day.

---

### Post by jnicita on 2006-10-14
moving post

---

