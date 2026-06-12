---
title: "[SOLVED] Flash Plugin Problem"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-12-10
Hello everyone, i have problem, i did not have any difficulties before with flush, i erased previously Ubuntu and installed Xubuntu and i had to enable restricted extras in order to use flash, Now i erased Xubuntu and using Ubuntu and from that time on i cant install flash for Firefox. 

Before browser used to find and install easily, now it install but gives me this error msd5 something i dont remember exectly sorry FLASH MISS INSTALLED PLUGIN, so it says its not installed properly and asking me do reinstall it, i did trhough add or remove and trhough sunaptic dozen of times and still same, i cant view videos on utube, MAN BECOUSE OF XUBUNTU I AM EXPERIANCING THIS DIFFICULTIES NOW, 

The only way i can intsall flash is trhough wine for windows and it allows  to watch, but old linux flash doesn work anymore for some reason

---

### Post by ddrplayer512 on 2007-12-10
My answer is in the next post. Accidentally posted this twice.

---

### Post by ddrplayer512 on 2007-12-10
My suggestion would be to go to:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")

Download the .tar.gz file into a new folder in your home directory (like for example /home/*username*/temp) and go into that directory and right-click the file and select extract.

Now open a terminal and type this (assuming that the folders are correct):

```
cd /home/*username*/temp/install_flash_player_9_linux/

```
 "username" refers to your username.

Then type this:

```
./flashplayer-installer
```

Follow the prompts, make sure all browsers are closed, and there you have it! That user has the flash player installed. You will need to do this for every user. Also, it works on Firefox and other Mozilla-based browsers.

Hopefully that worked. I have to do that all the time!!
Wish you the best!

-ddrplayer512

---

### Post by Taras on 2007-12-10
Ohh thanks a lot mate

---

### Post by ddrplayer512 on 2007-12-10
No problem! :)

---

### Post by nikoPSK on 2007-12-10
please mark this thread as "SOLVED".

---

### Post by boriquajake on 2007-12-10
Wow, I was having the same problem. You have to love the search feature. Heh heh. Anyway, thanks.

---

### Post by Taras on 2007-12-10
How do mark this as solved ?

---

### Post by Taras on 2007-12-10
ddrplayer512 thanks a lot to you, it worked so well i was typing in commands as u said and it worked veyr well and fast, when i was using trhough normal i think its called GUI it took so slow, but trhough terminal it was very fast, thanks a lot again !!!!!!!! me very haappy now!

---

### Post by nikoPSK on 2007-12-10
thread tools > mark this thread solved.

---

### Post by daradib on 2007-12-10
See this for more information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

