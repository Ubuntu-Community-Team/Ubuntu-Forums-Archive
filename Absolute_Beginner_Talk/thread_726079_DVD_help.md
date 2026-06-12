---
title: "DVD help"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by SteveHell on 2008-03-16
I'm having trouble with getting DVD's to play in totem and vlc. I followed a few post and non seemed to help until I found a post that sent me to here [http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html]("http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html")
I did those commands and now totem doesn't cry about not being able to play or vlc just crashing out. How ever my screen looks all funny like. here a screen shot.
[[IMG]http://img406.imageshack.us/img406/705/screenshotlq5.th.png[/IMG]](http://img406.imageshack.us/my.php?image=screenshotlq5.png)
what went wrong? how can I fix this.

oh btw I'm a new Linux user only 3 days old

---

### Post by Ub1476 on 2008-03-16
Here's the official guide for DVD playback: [RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

I believe you already got everything done there though. 

Do you have graphic drivers installed?

```
#Will show graphic card:
lspci | grep VGA
```

Installing Ubuntu-Restricted-Extras (Flash, Java, codecs etc), doesn't hurt either:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SteveHell on 2008-03-16
> **Ub1476 said:**
> Here's the official guide for DVD playback: [RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

I believe you already got everything done there though. 

Do you have graphic drivers installed?

```
#Will show graphic card:
lspci | grep VGA
```

Installing Ubuntu-Restricted-Extras (Flash, Java, codecs etc), doesn't hurt either:

```
sudo apt-get install ubuntu-restricted-extras
```

yes I ran the Ubunta-Restricted_Extra seemed to go well didnt get errors or anything.
also i ran
lspci | grep VGA
and got this 
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

---

### Post by Ub1476 on 2008-03-16
Is graphic driver installed from System>Administration>Restricted Driver Manager?

---

### Post by handydan918 on 2008-03-16
Perfect. Did you install the nvidia driver? That will help, if you haven't already done it.

---

### Post by SteveHell on 2008-03-16
yes I'm pretty sure I did that when I first installed the distro.

Okay I fixed it. After posting I tried again and still had that crazy screen look so I thought I try a video I got from this forum tux vs windows and it too had the crazy screen. sooo I thought okay let reboot and BAM! i have clean vid

[[IMG]http://img329.imageshack.us/img329/28/screenshot1op7.th.png[/IMG]](http://img329.imageshack.us/my.php?image=screenshot1op7.png)

thanks a bunch guys.

tis movie time! :guitar:

---

