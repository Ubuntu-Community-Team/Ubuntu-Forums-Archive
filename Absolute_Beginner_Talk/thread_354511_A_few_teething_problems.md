---
title: "A few teething problems"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by NSRMW on 2007-02-06
Hi, firstly I would like to say how much I like Ubuntu it looks great and I am just getting a feel for it but.....

I have two problems which I cannot seem to solve.

Firstly I cant get my sound to work I was using my onboard sound which is Realtek ALC 665 I believe so after hours of trying to get that to work following every tutorial I could find I disabled it and put in a SB LIVE 0220 which I also cant seem to get working.

Secondly my wireless card does not work either which is a BT Voyager 1040 (BCM4603) I have followed all the tutorials on here for that too and still found no joy :mad: 



I will stick with it for awhile as I do really like Ubuntu but I must admit life was much easier on windows but ubuntu and windows both have their down sides.

Thanks to anyone who can offer any advice or any help, I am willing to try anything.

---

### Post by Gannin on 2007-02-06
Welcome to Ubuntu :).

If you go to System > Administration > Device Manager, or System > Control Panel > Device Manager, depending on what version of Ubuntu you use, does it list anything about either one of your sound cards?

---

### Post by NSRMW on 2007-02-06
Device manager currently shows the SB0220 as I disabled the onboard sound when I added the Sb0220

---

### Post by mikewhatever on 2007-02-06
Hi,
I kind of understand your frustration, since in the beginning, I felt this way too. I my case, it only took a few days to solve the problems, you case may be a little harder, but I don't really know. Hopefully, someone with exactly the same or similar hardware will see your post soon enough and help you. If not, there is still hope. Split your post into sound problem and wireless problem. Ask specific questions. Specify the guides you've followed. Post the outcome of test commands. In other words, provide more information.

[Wireless Page]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless")
[Sound Page]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29")

---

### Post by Gannin on 2007-02-06
If you go to Applications > Accessories > Terminal and type in "alsamixer", does it show anything interesting?

---

### Post by NSRMW on 2007-02-06
Yes I can see a mixer

[AlsaMixer v1.0.10 (Press Escape to quit)]&#9474; 
Card: SB Live 5.1 [SB0220]  &#9474;&#9474; Chip: SigmaTel STAC9708,11                                                   &#9474;&#9474; View: [Playback] Capture  All&#9474;&#9474; Item: 3D Control - Switch [Off]


I can confirm master and pcm are set on

---

### Post by NSRMW on 2007-02-06
Ok after abit of messing about I now have some sound on the SB0220 only thing is its low and distorted.

---

### Post by Gannin on 2007-02-06
When you check "alsamixer", what level is PCM set at?

---

### Post by NSRMW on 2007-02-07
They was all set at 100, I messed around with my settings and now have full sound :)

thanks to everyone who helped.


Now all I need is this wireless network card working and I will stick with ubuntu, I will even consider buying a new card so are they any that work out of the box with no need for me to configure to much?

---

### Post by Gannin on 2007-02-07
Glad to be of help :).

When the volumes are set at 100, everything's going to distort.

As for your wireless question:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by muguwmp67 on 2007-02-07
Try these threads to get your wireless working, ndiswrapper looks like the best route.

[http://ubuntuforums.org/showthread.php?p=2027150#post2027150]("http://ubuntuforums.org/showthread.php?p=2027150#post2027150")
[http://www.ubuntuforums.org/showthread.php?t=319939]("http://www.ubuntuforums.org/showthread.php?t=319939")

---

