---
title: "buntu  doesn't have Beryl in respository"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by It_Was_Luck on 2007-10-27
ell... I got ubuntu7.10 just today, and I went to get Beryl from the add/remove programs thing and it wasn't there, and yes I has it on All available apps.

When I used version 7.04 it was there, why is it not there now.

Also where else can I get it?

---

### Post by overdrank on 2007-10-27
> **It_Was_Luck said:**
> ell... I got ubuntu7.10 just today, and I went to get Beryl from the add/remove programs thing and it wasn't there, and yes I has it on All available apps.

When I used version 7.04 it was there, why is it not there now.

Also where else can I get it?

Hi and I would just recommend adding a feisty repo and install that way
The first thing we need to do is add the security key, do this by pasting into a terminal:

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Then type in:

```
gksudo gedit /etc/apt/sources.list
```

This will open a file, add this to the very bottom by pasting:
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Then save and exit.

You will need to update again, so paste into a terminal:

```
sudo apt-get update
```

BERYL
Now to install Beryl (and Emerald window decorator) paste this into a terminal:

```
sudo apt-get install beryl beryl-manager beryl-core beryl-plugins beryl-settings emerald emerald-themes
```

---

### Post by santiagoward2000 on 2007-10-27
> **It_Was_Luck said:**
> ell... I got ubuntu7.10 just today, and I went to get Beryl from the add/remove programs thing and it wasn't there, and yes I has it on All available apps.

When I used version 7.04 it was there, why is it not there now.

Also where else can I get it?

Well, the Beryl project is no longer being developed. The team got back together with Compiz, and they're now working on Compiz-Fusion, which is already installed in K/Ubuntu Gusty. To activate it you should install CompizConfig Settings Manager (it's in Synaptic) and configure it.

---

### Post by It_Was_Luck on 2007-10-27
Okay well I have gusty so I went anf installed the compiz settings manager, but I can't figure out how to use it, heck I can't even find it.

---

### Post by llamakc on 2007-10-27
System | Preferences | Advanced Desktop Effects Settings

---

