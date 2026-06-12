---
title: "Download wine?"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by Game master pro on 2005-09-10
I have ubuntu on a computer without the internet, i can't find wine already installed so i though i would just download it and put it on the other computer, but there is no "click here to download" link, you have to use apt-get. How would i go about installing wine?
[wine site](http://www.winehq.com/)

---

### Post by weasel fierce on 2005-09-10
the wine website has some directions on how to add it to your repositories, then you can apt-get it, as well as any dependencies

---

### Post by online14230 on 2006-10-03
Nice reply. I believe you have the same problem I have. Try browsing the repositories using IE and download it. Good luck, because it takes very long. You have to download Wine and ALL its depends, which are too numerous to mention. Oh yeah, dont forget to get the depends depends... and their depends too. Yes, I know. Thats a LOT to d/load. Once you have all, "sudo dpkg -i *.deb" works wonders from the folder youve copied them to...
Have fun.

Just for your info, Im STILL downloading dependencies, which Ive been doing for three days straight now.
b.

---

### Post by Josh1 on 2006-10-03
Erm..
```

sudo aptitude install wine

```
Then once its installed:
```

winecfg

```

;).
- Josh

edit:
Changed apt-get to aptitude, thanks xpod ;).

---

### Post by xpod on 2006-10-03
```
sudo aptiude install wine
```

Is that not the better choice if theres so many dependancies??
I got wine and practically everything else via automatix mind you
and it dont come much simpler than that....:mrgreen:

---

### Post by Josh1 on 2006-10-03
> **xpod said:**
> ```
sudo aptiude install wine
```

Is that not the better choice if theres so many dependancies??
I got wine and practically everything else via automatix mind you
and it dont come much simpler than that....:mrgreen:

Sorry,
I forgot to put aptitude, I usually don't uninstall programs, since I usually only install the things I need. :).
Original post edited, thanks for the tip.
- Josh

---

