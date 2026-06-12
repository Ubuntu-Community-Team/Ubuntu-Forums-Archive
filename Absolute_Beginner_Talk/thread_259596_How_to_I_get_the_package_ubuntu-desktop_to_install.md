---
title: "How to I get the package ubuntu-desktop to install GNOME on Kubuntu?"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by abossy on 2006-09-17
I have Kubuntu installed on my laptop. I believe it's the latest version of Dapper, and it's the amdx64 version. I'd like to give GNOME a whirl, but I am totally lost as to how to get the package ubuntu-desktop. 

Firstly, if I open adept and click "Update," no ubuntu-desktop shows up. Secondly, if I type something like "sudo aptitude download ubuntu-desktop," it says that the package cannot be found. If I try the regular install (sudo aptitude install ubuntu-desktop), naturally, it says the package cannot be found.

So how the heck do I get it!? I googled it, landed on the ubuntu desktop page, and downloaded the Dapper version, because (*I think*) it corresponds with the kubuntu version I have. (What's the difference between dapper, edgy, breezy, etc. anyway? The dapper version is the smallest version number out of all of them, 0.19) What do I do now?

Thanks!
Adam

---

### Post by Perfect Storm on 2006-09-17
```
sudo aptitude install ubuntu-desktop
```

Have you checked your sourcelist?

any error output when running:
```
sudo aptitude update
```

---

### Post by whizbaby on 2006-09-17
And don't be afraid to remove *kubuntu-desktop* if you are asked, because it's only a bundle of references to the kubuntu packages. By the way you don't have to install ubuntu-desktop to have gnome, you can install the package *gnome* (and aditionnaly any other package starting with *gnome*)

---

### Post by abossy on 2006-09-17
Nope, update seems to run fine.

How do I access the sourcelist? I can't find it. 

Thanks for helping a n00b,
Adam

---

### Post by abossy on 2006-09-17
> **whizbaby said:**
> And don't be afraid to remove *kubuntu-desktop* if you are asked, because it's only a bundle of references to the kubuntu packages. By the way you don't have to install ubuntu-desktop to have gnome, you can install the package *gnome* (and aditionnaly any other package starting with *gnome*)

I have the same problem with the GNOME package as I do with the ubuntu-desktop one; it doesn't exist. Plus, if I installed GNOME without the entire ubuntu-desktop package, wouldn't there be a bunch of dependencies on other programs that would cause problems?

Thanks,
Adam

---

### Post by bulldog on 2006-09-17
Sources.list is 

gksudo gedit /etc/apt/sources.list

Make a copy first

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

Now you can uncomment [remove #] the neccessary repositories.

Could be done in synaptic too.

When you alter your sources.list be sure to update

sudo aptitude update

sudo aptitude install ubuntu-desktop

and it should work

---

### Post by jordanmthomas on 2006-09-17
Actually, gedit won't be installed since it's part of gnome
you need
```
kdesu kwrite /etc/apt/sources.list

```

and synaptic should be adept

---

### Post by whizbaby on 2006-09-17
> **abossy said:**
> I have the same problem with the GNOME package as I do with the ubuntu-desktop one; it doesn't exist. Plus, if I installed GNOME without the entire ubuntu-desktop package, wouldn't there be a bunch of dependencies on other programs that would cause problems?

First of all:
*/etc/apt/sources.list*
Then
GNOME basically only is a window manager like KDE, XFCE, enlightenment etc...
The gnome package installs
[I]gnome-desktop-environment (= 1:2.12.2.3), gnome-office (= 1:2.12.2.3),
gdm-themes, gnome-cups-manager (>= 0.30), gnome-themes-extras, rhythmbox (>= 0.9.2), synaptic (>= 0.53.4) | gnome-apt, gnome-screensaver | xscreensaver[/I]
Ubuntu-desktop adds a crowd of applications associated with gnome to it (see by *apt-cache search ubuntu-desktop --full|less*)

---

### Post by jordanmthomas on 2006-09-17
I feel like such a nazi...but Gnome is a desktop environment (like KDE, XFCE, enlightement, etc...)
By default, it uses metacity as its window manager.

**apologizes again and goes away**

---

### Post by whizbaby on 2006-09-17
Jawohl, Herrrrr Gennerrral, gnome ist kein Window-Managerrrr sonderrn ein Desktopp-Envirrronment!

---

### Post by bulldog on 2006-09-17
> **jordanmthomas said:**
> I feel like such a nazi...but Gnome is a desktop environment (like KDE, XFCE, enlightement, etc...)
By default, it uses metacity as its window manager.

**apologizes again and goes away**

Yes,please do :biggrin: 

But you're totally right I was mistaken with gedit and gksudo and all that.

[Gnome user by default]

---

### Post by abossy on 2006-09-17
Excellent! Apparently a bunch of important lines were commented out in my sources.list file during installation because I had no internet access when I installed. 

So... I installed ubuntu-desktop and it gave me a sort of bare-bones version of Gnome with firefox installed, but nearly everything else is from KDE. Additionally, I have this boring desktop and no options to change.  whizbaby, you say all associated packages are installed with ubuntu-desktop. I hoped I would get a GNOME install similar to the one on my desktop, which uses the regular Ubuntu installation. Do I need to install things myself, or is there an easier way to get a richer GNOME running?

---

### Post by whizbaby on 2006-09-17
> a crowd of does not necessarily mean *all* gnome-related packages are installed. Look for gnome in *favourite_package_tool*. However, some packages overlap in kubuntu-/ubuntu-desktop, so a slight deja-vu can be expected. Can you precise a little what you're looking for ?

---

### Post by abossy on 2006-09-17
> **whizbaby said:**
> does not necessarily mean *all* gnome-related packages are installed. Look for gnome in *favourite_package_tool*. However, some packages overlap in kubuntu-/ubuntu-desktop, so a slight deja-vu can be expected. Can you precise a little what you're looking for ?

Nothing specific, unfortunately. I hoped it would more closely resemble the default install that comes with Ubuntu. There are no themes, for example; the theme package has to be installed seperately. I'll tinker with it I suppose. 

Thanks,
Adam

---

