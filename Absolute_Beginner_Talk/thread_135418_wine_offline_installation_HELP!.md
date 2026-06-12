---
title: "wine offline installation HELP!"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by dagamer on 2006-02-23
can someone please tell me how to install wine offline because i have dialup 
 


or someone could tell me how to dial a modem in ubuntu

PLEASE HELP

---

### Post by Sutekh on 2006-02-23
- You can download the latest version of wine as a debian package (a .deb file) from [http://wine.sourceforge.net/apt/breezy/]("http://wine.sourceforge.net/apt/breezy/")

 - Here's the link to the .deb

[http://wine.sourceforge.net/apt/breezy/wine_0.9.8-winehq-1_i386.deb]("http://wine.sourceforge.net/apt/breezy/wine_0.9.8-winehq-1_i386.deb")

 - Once you get this file (and I assume that you will be using Windows or something to download this, not Ubuntu), you should copy the file over to Ubuntu.  A USB flash drive would be easiest.  A CD would also be pretty easy.

 - When you copy the .deb into Ubuntu, just put it on your Desktop

 - Open a terminal window (In the Applications -> Accessories menu), and use **cd** (just like DOS) to navigate to your Desktop (or wherever you put the .deb)
```
cd ~/Desktop
```This will change directory to your Desktop (~/ corresponds to your home folder - /home/<username>)

 - When you have changed to the folder with the .deb, you can install wine using this command
```
sudo dpkg -i wine_0.9.8-winehq-1_i386.deb
```

---

### Post by dagamer on 2006-02-23
now can anyone tell me how to dial a modem in ubuntu
:-|

---

