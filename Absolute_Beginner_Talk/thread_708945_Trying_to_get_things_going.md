---
title: "Trying to get things going"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by slickh20 on 2008-02-26
ok so i am trying to set up everything just installed the OS!

I have a few problems.. no internet and i cant change the appearence settings. see screen shots below.

my linksys usb wireless car sees the router but diesnt like the passphrase i put in that does work on  other computers.  is there something i am missing or more i can do?

the video thing i have no idea... any help you have would be great.  i am not a total computer noob just definatly new to ubuntu.

---

### Post by chris.a.barker on 2008-02-26
Congratulations on you new installation. First the video card.

1. You will need to go to system->administration->synaptic package manager
2. Next within synaptic go to settings->repositories
3. Make sure the box labeled "Proprietary Drivers For Devices" is checked.
4. At the bottom of the box uncheck your CDROM media.
5. Click close.
6. Open the terminal and type:
```
sudo apt-get update
```
7. Enable you video drivers.

Happy Days...hopefully!

---

### Post by chris.a.barker on 2008-02-26
Are you sure you are selecting the right type of encryption for your wireless network? Not to insult your intelligence or anything.

Additionally, if you are using WPA-2 the linux driver you are using may not support WPA-2. 

Just a thought.

---

### Post by spiderbatdad on 2008-02-26
```
sudo apt-get install nvidia-glx-legacy
``` in a terminal, or open the synaptic package manger: System>>Administration>>Synaptic Package Manager: which may be preferred, as there are some devs as well. But you will need a working internet connection to download them.

That passphrase is not your password, as far as I know, but a WEP or WPA key.

---

### Post by slickh20 on 2008-02-27
don't worry, insult all you want just keep the help coming.

well i know i have the right key because i logged into the router and the key that i put in there is the same as well as the encryption i don't know much about the shared or pen key but neither do the trick.

the router is identifying my computer as i have it named desktop 1 and it also sees all of my other computers. ??? 

i am already starting feel like i am going to be a frequent poster on here.:)

the other video stuff light have worked if the internet was working. ill get back to that.

---

### Post by slickh20 on 2008-02-27
ok all of a sudden after 30 tries it works ill ask again if i have trouble with the drivers.. thanks all!!!

---

### Post by chris.a.barker on 2008-02-27
Godspeed slickh20

---

### Post by slickh20 on 2008-02-27
ok i got the drivers working... but now it wont let me uo the visual effects says "desktop effects could not be enable" and then i think it laughed a little at me.


what do i do with all the repository or updates that i had it down load? (i did the two terminal comands that were given to me) 

are they install if you want or are they all recomended installs?

---

### Post by spiderbatdad on 2008-02-27
run ```
sudo apt-get update
```in your terminal and you should be able to enable the proprietary driver in System>>Administration>>Restricted Drivers Manager, for your visual effects. You will also need to install compizconfig-settings-manager from synaptic. There are quite a few guides to getting compiz going in the forum.[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200)
For example.

---

### Post by igknighted on 2008-02-27
> **slickh20 said:**
> ok i got the drivers working... but now it wont let me uo the visual effects says "desktop effects could not be enable" and then i think it laughed a little at me.


what do i do with all the repository or updates that i had it down load? (i did the two terminal comands that were given to me) 

are they install if you want or are they all recomended installs?

I believe that the legacy nvidia drivers (7xxx series) do not support compositing and cannot be used with Desktop Effects.  To confirm, what are the outputs of the following commands:
```
lspci | grep VGA
```
and
```
glxinfo | grep direct
```

---

