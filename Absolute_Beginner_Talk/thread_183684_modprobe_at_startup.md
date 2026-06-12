---
title: "modprobe at startup"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by nikolaos on 2006-05-28
I just configured my wireless card and i am wondering. Is there a way to modprobe automatically on boot time instead of ...

```
sudo modprobe ndiswrapper
```

...all the time, and....
is the answer similar with every module i want in or out of the kernel????

---

### Post by joshrobinson on 2006-05-28
[QUOTE=nikolaos]I just configured my wireless card and i am wondering. Is there a way to modprobe automatically on boot time instead of ...

```
sudo modprobe ndiswrapper
```

...all the time, and....
is the answer similar with every module i want in or out of the kernel????[/QUOTE]

add a script into your /etc/init.d folder named whatever you want.. say script.sh

put inside it the code you want to run.. in this case sudo modprobe ndiswrapper
you can also throw in your dhclient commands and wpa_supplicant line if you need it

then in a terminal do

sudo update-rc.d script.sh defualts

it should run that line for you now on boot

---

### Post by nikolaos on 2006-05-28
Thank you for such a sort notice. It works just fine

---

### Post by phoboulinos on 2006-06-17
Vlakies leei o apo pano sou ... skatonoumpades...

---

### Post by stupidkid on 2006-06-17
A very simple way is to jsut add ndiswrapper to /etc/modules. I'm in Gentoo right now, so I could be wrong regarding the file name.

---

