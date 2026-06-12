---
title: "Utorrent playing up"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by bagguley on 2007-04-16
Hey

I've used ubuntu for a month or so now and have really enjoyed it (Windows is long since wiped from my machine). I have a slight problem though.

Ive used utorrent via wine and has worked perfectly up until now. I had to do a fresh install thus losing all my additional programs (yes, i now have aptoncd ready for the next upgrade). I installed utorrent in exactly the same way i have before (even used the same instruction page) but for some reason now, once installed it will not allow me to load torrents to it. It wont allow unix address (/home/john/desktop etc).

Any ideas? You help will be greatly appreciated!

---

### Post by amaroKer on 2007-04-16
Umm, are you hell-bent on using uTorrent?  I can't help you with your uTorrent problem, but BitTornado is an amazing torrent client easily installed by:

```
sudo aptitude install bittornado bittornado-gui
```

---

### Post by Tsen on 2007-04-16
To be frank, uTorrent totally kicks BitTornado's butt.
And everything else's.
No idea how to solve the problem, though :(

---

### Post by zvacet on 2007-04-17
Put exe in some folder in home directory.After that

```
wine /home/your_username/folder_of_choice/utorrent.exe
```

This is way I installed following instructions on the page I don´t remember anymore.I hope you will install it,because I know what are you missing.

---

### Post by david_kt on 2007-04-17
Just use the standalone utorrent, download it from [here.]("http://download.utorrent.com/1.6.1/utorrent.exe") No installation required.

For example, you could put it on your desktop, and right click and run with wine or just double click it if wine is default. It will appear on notification area on your top right hand corner. To show or hide it, double click on the icon.

For me, I put it on my home/username/bin folder. It automatically put a launcher in my desktop when I run it the first time. And then I move the launcher to panel (click and drag to panel).

DK

---

