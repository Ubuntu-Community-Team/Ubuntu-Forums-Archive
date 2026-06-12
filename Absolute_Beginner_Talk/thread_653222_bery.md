---
title: "bery"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by akash238 on 2007-12-29
i have ubuntu 7.04 
i am trying to put that beryl thing on there
can anybody help me

i just installed ubuntu so i am a complete noob at this whole linux thing

---

### Post by overdrank on 2007-12-29
> **akash238 said:**
> i have ubuntu 7.04 
i am trying to put that beryl thing on there
can anybody help me

i just installed ubuntu so i am a complete noob at this whole linux thing

Hi and could you tell us the model of your graphics card?

---

### Post by akash238 on 2007-12-29
i have the nvidia 8600 gtx 512 mb

---

### Post by overdrank on 2007-12-29
> **akash238 said:**
> i have the nvidia 8600 gtx 512 mb

Ok have you enable the restricted drivers under system, administration? Once you have them install and working then you can 

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

AND VOILA! Beryl is installed, to start it simply use the alt, F2 key and enter

```

beryl-manager
```

You may need to change the window manager, do this by right-clicking the beryl icon and selecting Beryl from the 'Select Window Manager' menu.

---

