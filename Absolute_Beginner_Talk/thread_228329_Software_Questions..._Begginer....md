---
title: "Software Questions... Begginer..."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by tgdrums1990 on 2006-08-03
OKay i have used wiondows my whole life. I am 16 years old and decided to stop using illegal prgrams i have and go for somthing more astable and non illegal. ANyways i want to know if there is a program ou there that is like Dreamweaver for Ubuntu. I need aporgram like that... I am looking for an exsperinced user to add me to there aim, yahoo, or msn messenger so i can talk about pop questions instead of always coming to the board for things.. My user name is tgdrums1990 for aim and yahoo and [email]tgdrums1990@hotmail.com[/email] for msn. I have many questions and have never ever been good at posting on forums...

---

### Post by aysiu on 2006-08-03
Nvu, Quanta, Screem, Amaya, Bluefish.

I prefer Gedit myself...

Make sure you read this first:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by tgdrums1990 on 2006-08-03
[FONT="Arial"]Okay well i updated it, but it dose nuthing, i cant find it anywhere. I installed Quntaplus, but im not familure with those types of html editors. Is there anysoftware like dreamweaver availiable. Maybe that one you pointed out is.. But i dont think i may have installed it right. Im sure here in a few months i will be pro at using this, but for right now, much guidence is needed, thanks. Feel free to add me at tgdrums1990 is my screen name for aim and yahoo and [email]tgdrums1990@yahoo.com[/email] is my screen name ofr msn... [/FONT]

---

### Post by aysiu on 2006-08-03
Type ```
quant
``` in the terminal and before you press **Enter**, press **Tab** twice. It should fill in the command. I believe the command is ```
quanta
```

Just so I can see that you installed it correctly, can you post the output of this command? ```
sudo aptitude update && sudo aptitude install quanta
```

---

### Post by Hexx on 2006-08-03
Try NVU. It's a bit like DreamWeaver. Its website is [here]("http://www.nvu.com/index.php").

You can install it by opening Terminal and typing:

```
sudo aptitude install nvu
```

---

### Post by tgdrums1990 on 2006-08-03
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [65.7kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [45.5kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [44.2kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [11.0kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Fetched 234kB in 1s (151kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  gnome-screensaver libnautilus-extension1 nautilus nautilus-data
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Here the responce you ask of... I tried thet thing the other post sugested and it did nuthing... I wish i could get the hang of this a little better.. Any feel free to add me, tgdrums1990 is my screen name for both aim and yahoo, and [email]tgdrums1990@hotmail.com[/email] is my screen name for msn... It would be a big help if someone could add me. When giving directions please give start to finish set of directions, it took me ffor ever to figure out that i need to run terminal to get what was asked to be done...

---

### Post by aysiu on 2006-08-03
Okay. Looks as if it's installed.

Theoretically, you should be able to launch it by going to Applications > Internet > Quanta.

If you don't see it in there, press **Alt-F2** and a box will come up. In that box, type ```
quanta
``` and the Quanta program should run.

You can also add Quanta to the menu (if it's not already there) by right-clicking on **Applications** and selecting **Edit menus**. Then go to **Internet** and click on **File** and **New item** to add a new entry. The title of the entry should be *Quanta* and the command should be ```
quanta
```

---

### Post by tgdrums1990 on 2006-08-03
Oh okay, well yes the quanta program is there. I think we have misunderstood each other, my question is are there any webdesigh prgrams that have a desighn veiw vs. code veiw. I loved dreamweaver because it had tons of flash things and was very easy to get the hang of, i felt. Dose Quantum have a desighn view and if so, how do i slect it, cause when it loads it loads in a code veiw, which since im not a very good code writer at all weret alking, basic basic, a desighn veiw suits me so much better... How do i get the irc channels to work...

---

### Post by Hexx on 2006-08-03
NVU has a design view. See my post above for info.

---

