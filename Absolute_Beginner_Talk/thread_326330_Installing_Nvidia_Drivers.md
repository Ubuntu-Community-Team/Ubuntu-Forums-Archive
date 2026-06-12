---
title: "Installing Nvidia Drivers"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Griffongob on 2006-12-27
hello all...again haha I was able to update to 6.06 and now want to tackle getting my Nvidia 7900 GT card working but first I have a couple of questions. 1. How in the world do you do this and 2. will it affect my performance on Windows?

---

### Post by taurus on 2006-12-27
1.  Here you go...
[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

2.  It has nothing to do with Windows.

---

### Post by Griffongob on 2006-12-27
hmm looks like I have to upgarde to 6.10 before I can install them right?

---

### Post by taurus on 2006-12-27
Actually, just replace the edgy with dapper and you are all set.  No need to upgrade if you don't want to.

[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by Griffongob on 2006-12-27
I type 

    wget [http://www.albertomilone.com/drivers/tseliot.asc](http://www.albertomilone.com/drivers/tseliot.asc)

 into the terminal right?

---

### Post by taurus on 2006-12-27
Yes, type these three commands from a terminal.

```

wget http://www.albertomilone.com/drivers/tseliot.asc
gpg --import tseliot.asc
gpg --export --armor albertomilone@alice.it | sudo apt-key add -

```
Then, continue with the instructions.

---

### Post by Griffongob on 2006-12-27
almost got it I have get some other package first it seems

---

### Post by taurus on 2006-12-27
You just have to install a source for your kernel, either 386 or generic...  Then, you can install the nvidia-glx.

---

### Post by Griffongob on 2006-12-27
YES ITS WORKS!!! ok any suggestions of what next to install its a fresh install so nothing is on it

---

### Post by taurus on 2006-12-27
I assume you are running Gnome!  Now, download and install automatix2.  Then use automatix2 to install all the codecs (so you can play your mp3s and movies), lastest flash plugins, Google Earth, and a bunch of other goodies...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Griffongob on 2006-12-27
hmm I just tried using my wireless card its wierd Ubuntu sees its there but when I unplug the ethernet cable the wireless network I have set up isnt given as an option network manager only says Wired network greyed out. I'm using a linksys WMP54G

---

### Post by Griffongob on 2006-12-27
Oh and thanks for automtix I'm using it right now

---

