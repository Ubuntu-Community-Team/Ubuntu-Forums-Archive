---
title: "[SOLVED] Ie"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-08-25
Hi All

I have been browsing the gallery a bit and have seen a few Ubuntu desktops that seem to show Internet Explorer icons(one of them, upsidedown).  

Is that real, or some kind of clone?:popcorn:

---

### Post by wh0rd on 2007-08-25
Yeah it's real. Check out:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by Xoanan on 2007-08-25
> **wh0rd said:**
> Yeah it's real. Check out:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Wow!  Outstanding! I will have to give that a try!

Thanx!:)

---

### Post by Xoanan on 2007-10-03
Hey, sorry to bother everyone, but what is the rest of this line? There is an ad on the page that is blocking it.  grrrr!

 wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key ac

---

### Post by Terl on 2007-10-03
Here is the page you asked about:

> You have to enable universe packages first. It is also recommended that you use the official winehq ubuntu package: 

1) Open a terminal 

2) Open /etc/apt/sources.list 

 sudo gedit /etc/apt/sources.list
3) Uncomment (or add) following lines: 

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
4) Add this line: 

 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
5) Close gedit. Update and install wine and cabextract: 

 wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract
6) Download IEs 4 Linux and install 

 wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux
Note for Dapper users: if you use ubuntu dapper, replace edgy with dapper on lines above. Note for Feisty users (7.04): if you use ubuntu Feisty, replace edgy with feisty in the lines above. Also replace gedit with kedit if running Kubuntu instead of Ubuntu. 

For "Fiesty" K/Ubuntu Users (and 64-bit "Fiesty): [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) 



---

### Post by Xoanan on 2007-10-03
Ah!  Thanx!:popcorn:

---

### Post by Xoanan on 2007-10-03
Got it installed gang!  Thanx!

---

