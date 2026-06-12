---
title: "Processor fan / Should use Xbuntu ?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Delawaredave on 2008-01-09
Noobie.   1500 MHz Sony with 512 Mb.   Installed Ubuntu, dual boot.

Install went fine - but two issues:

1.  The processor fan is on high speed all the time - annoying.   Booting with Windows has the fan off most of the time

2.  Ubuntu is not as "zippy" as I expected.   With this system, should I use Xbuntu instead ?

Thanks !

---

### Post by talsemgeest on 2008-01-09
What motherboard do you have?
And if it is not as "zippy" as you expected, try turning off the desktop effects. System>Appearances.

---

### Post by Paqman on 2008-01-09
I have a 1.5GHz Celeron laptop with 512MB RAM running Ubuntu quite happily. If you turn off desktop effects and notice a big improvement it means you graphics driver isn't quite up to scratch.

---

### Post by cub682 on 2008-01-09
Fan control on older Sony desktops is a problem. Some have reported success but takes quite a bit of tinkering.

[http://ubuntuforums.org/showthread.php?t=238566&highlight=%2Fusr%2Fsbin%2Ffancontrol](http://ubuntuforums.org/showthread.php?t=238566&highlight=%2Fusr%2Fsbin%2Ffancontrol)

---

### Post by Delawaredave on 2008-01-09
Thanks for note. 

I think it is a Sony PCV-R526DS - about 6 years old with an Asus motherboard P2B-AE  Rev 1.02

Under Windows, the fan is usually off, then turns itself on sometimes when there's a lot of compute intensive stuff.   Thanks.

---

### Post by mali2297 on 2008-01-09
Why don't you try out  [xfce4]("http://packages.ubuntu.com/gutsy/x11/xfce4") to see if you get any improvement? Install the package via Synaptic, then you can choose xfce using the session selection dialog at login.

---

### Post by Delawaredave on 2008-01-09
> **cub682 said:**
> Fan control on older Sony desktops is a problem. Some have reported success but takes quite a bit of tinkering.

[http://ubuntuforums.org/showthread.php?t=238566&highlight=%2Fusr%2Fsbin%2Ffancontrol](http://ubuntuforums.org/showthread.php?t=238566&highlight=%2Fusr%2Fsbin%2Ffancontrol)

Hey - how'd you find that ?  I searched - thanks.

I turned off "appearance stuff" and will look into xfce4.

Thanks for everyone's help !  Dave

---

### Post by hyper_ch on 2008-01-09
actually, you could easily install xfce/xubuntu:

```

sudo apt-get install xubuntu-desktop

```

It will then download and install the xubuntu specific stuff. All you need to to then is log out and log back in again but upon the login screen select xfce as session.

---

