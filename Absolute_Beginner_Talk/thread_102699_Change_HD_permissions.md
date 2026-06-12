---
title: "Change HD permissions"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by McK on 2005-12-12
Ok, this is weird, I'm not allowed to read/write/edit any of my harddrives ( at media, they all have a red cross over them )

If I click them it says i don't have enough rights to view the content of my disk,
BUT if i first go to "disc stations" and then open them, i can view the content

help please :/

---

### Post by DiscoKiller on 2005-12-12
I`m no expert but i think this may help. Go to 'run as different user' run nautilus as 'root'. find your way in nautilus to the 'media' folder and right click on anything you wish to edit the permissions for. go to properties and select the permissions tab. i`ll leave it to your discretion as to what you want to change in there but by running nautilus as root this will enable you to change the permissions.

DK

---

### Post by aysiu on 2005-12-12
Are these Windows hard drives? If so, they need to be mounted properly.
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by McK on 2005-12-13
ok, i mounted them properly now, i gave them windows, windows2 and windows3 just to make it easy for me

but how do you delete the original directories?( like /dev/hhd1)

---

### Post by frodon on 2005-12-13
type in a terminal : ```
sudo rm -r /dev/hhd1
```it will delete the directory

---

### Post by McK on 2005-12-13
thx! 

oh yeah, another question

i managed to install my SB soundcard, but the default in alsamixer is my Nvidea Onboard sound

do you know how to change it to SB?

edit: nevermind i got it ;)

---

