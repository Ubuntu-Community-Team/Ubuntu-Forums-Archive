---
title: "No WiFi Signal Strength"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by andytof47 on 2007-01-13
Hi I have Edgy Installed and a WUSB54G Wireless Adapter.

When I used it in Dapper it worked without a glitch, However I have been running Edgy for about a week or two and from day one i haven't had a signal strength indicator......


I left it until now because it seemed un-important however i am now using kismet and although it works fine I really need to have an idea of the type of signal strength I am getting

Any help

---

### Post by tribaal on 2007-01-13
Well the one I use myself is nm-applet, along with NetworkManager. It's an applet that shows you the wireless signal streght, as well as managing your different Wifi profiles etc...

To install it, just do

```
sudo aptitude install nm-applet
```
And it'll install everything it needs to work.
If you already tweaked your wifi setup a little bit, you'll need to do the following as well:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.BACKUP
``` (Back up your interface configuration file)
and
```
sudo nano /etc/network/interfaces
```
Comment out (add a # in the beginning) every line exept the two first lines.
This should give you a fully functionning applet.


If you don't like it, just do a quick
```
sudo cp /etc/network/interfaces.BACKUP /etc/network/interfaces
```
```
sudo aptitude remove nm-applet
```
and you'll be back to normal.

Hope this is what you're looking for. :)

- trib'

---

### Post by andytof47 on 2007-01-13
Yeah I tried sudo aptitude get nm-applet but it can't find a package named that

which repo do i need enabled???


Cheers again

---

### Post by andytof47 on 2007-01-13
bump!!! Please

---

### Post by andytof47 on 2007-01-18
Hi After Going without for a few days I found I needed to install a patched version of the driver, because I am using it for wifi auditing.

Anyway the patch was just to get packet injection working, but to my suprise fixed the signal strength.......yay

[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)    (driver)

[http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide)

contains amongst other things a howto install

also the driver is not a standard driver - it is patched but if you can't find a normal one or want packet injection at least you have the link

toodles:cool:

---

### Post by MkfIbK7a on 2007-01-18
yes other people have posted this problem...

---

### Post by andytof47 on 2007-01-19
Yeah It's locking up the system like a dog now, ummmmm how do i remove the driver so that i can install 1.4 instead of the 1.4.9 i am using now


not sure if a new thread is needed but i didn't want to start one for something so closely related.....


Any help is appreciated

---

### Post by andytof47 on 2007-01-19
Actually I just installed the 1.4.0 after compiling it and I figure that since the module name is the exact same it should just overwrite the old one -------- is this exactly right????

Also I have read the readme and it talks about auto loading the module at boot, I assumed it would do so but it doesn't


Anyway I tried to follow the limited instructions and since i'm still new at this i'm wondering if anyone can write this down step by step



PLEEEEEEAAAAASSSSSSSEEEEEE


Thanks

---

