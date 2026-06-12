---
title: "BERYL/COMPIZ? Maybe? i dunno....?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Zackie on 2008-01-25
I want to get the stellar nice GUI of Beryl or "Compiz" i say that cuz i'm not sure if that is right.... I want to find a place to Dowload it and install... I'm a super user of windows and not use to Sourceing and  all that jazz... I just know what works... sorry for the stupidity.. but... i like the looks of beryl or that compiz thang... just want to know how to install and apply... and alll that jazz... Also... I'd like to thave the most recent updates for my sound/video cards.... if there is a way to bundle this into one reply rock on!!!


Much love,



Zackie...:guitar:

---

### Post by RomeReactor on 2008-01-25
Hi. Do you have Ubuntu installed, and if so, is your Ubuntu system connected to the internet? What video card do you have?

---

### Post by Zackie on 2008-01-26
internet is up and running supa fast and Ubuntu is on as well where can i find info on my video card ... it an NVida somthing.. its pretty good..

---

### Post by RomeReactor on 2008-01-26
To get information about your video card, open a terminal (Applications->Accessories->Terminal) and write or paste:
```
lspci | grep VGA
```
press ENTER, and post the output. To see which driver it's currently using:
```
cat /etc/X11/xorg.conf | grep Driver
```
and post that also (your video driver will be the last one listed). If it says **nv**, go to 'System->Administration->Restricted Drivers Manager' and check the case for your card. After that, go to 'System->Preferences->Appearance' and on the 'Visual Effects' tab, set it to 'Normal'.

---

### Post by Zackie on 2008-01-27
zackie@zackie:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
zackie@zackie:~$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"
zackie@zackie:~$

---

### Post by Ub1476 on 2008-01-27
You can enable Compiz-Fusion in System|Preferences|Appearance|Visual Effects

Make sure that you have installed the nvidia drivers in System|Administration|Restricted Driver Manager.

To get advanced effects, install Advanced Desktop Effects in add\remove or in terminal

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Zackie on 2008-01-27
That worked One quick question though... how do i get the fire pain to work? Do Hold down the super button the windows key and shift or control or what ever it was.. didn't work...

---

### Post by ugm6hr on 2008-01-27
> **Zackie said:**
> That worked One quick question though... how do i get the fire pain to work? Do Hold down the super button the windows key and shift or control or what ever it was.. didn't work...

Compiz-Fusion Wiki (Community Manual): [http://wiki.compiz-fusion.org/Plugins/Firepaint](http://wiki.compiz-fusion.org/Plugins/Firepaint)

---

### Post by Zackie on 2008-01-27
Rock on... It all works great and fun to mess with!!!


Peace out and rock bless'


Zackie...

---

