---
title: "I keep hitting a Brick Wall"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by kcgreg on 2006-09-17
](*,) ](*,) ](*,) 
Hi all,

I went through the unofficial dapper guide for Ubuntu which is this link [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) but I still cannot get macromedia flash player to work....whenever I go to a certain website to watch things through MFP Firefox keeps asking me to install missing plugins - shouldn't they already be there because when I type this into the terminal:

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

I get this response:

kcglinux@kcglinux:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kcglinux@kcglinux:~$ sudo update-flashplugin

So where am I going wrong?????](*,) ](*,) ](*,) 

This is frustrating!!! 

I managed to get Skype on board and Java I think without any hassles but this macromedia flash player is driving em up the wall...please help anybody!!!!

Kcgreg

---

### Post by nudnik on 2006-09-17
Click on the "install missing plugins" icon under Firefox, and let the browser install whatever it might require. This will probably do the trick, but after all this>> ](*,)  isnt the Ubuntu mascot for nothin' you know:biggrin:

---

### Post by gn2 on 2006-09-17
I had the same problem and solved it by using Automatix which installed it correctly for me.

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Anduu on 2006-09-17
You say "a certain site"...which site?

Can you watch videos on youtube?

---

### Post by kcgreg on 2006-09-17
> **Anduu said:**
> You say "a certain site"...which site?

Can you watch videos on youtube?

I don't know??? I don't even know if I have youtube???:confused:

---

### Post by Anduu on 2006-09-17
This is youtube...

[http://www.youtube.com](http://www.youtube.com)

---

### Post by linuxa on 2006-09-17
1) Go to [www.youtube.com](www.youtube.com) with Firefox
2) If you get some prompt in the main part of the screen to install macromedia flash player. Click the link, it'll take you to where you can download flash.
3) Navigate to the directory where flash is using Konsole
4) Uncompress the downloaded version of flash, a install_flash_player_7_linux directory should be created
5) Go to the new directory, there should be an executable there called flashplayer-installer
6) type: ./flashplayer-installer

---

### Post by kcgreg on 2006-09-17
> **gn2 said:**
> I had the same problem and solved it by using Automatix which installed it correctly for me.

[http://www.getautomatix.com](http://www.getautomatix.com)

Thaks bud - I have downloaded automatix but now it is saying that automatix couldn't download missing plugins at the moment, try again later.

This is so strange!!!

](*,) ](*,) ](*,) HELP!!! AAARGH!!!

---

### Post by kcgreg on 2006-09-17
> **linuxa said:**
> 1) Go to [www.youtube.com](www.youtube.com) with Firefox
2) If you get some prompt in the main part of the screen to install macromedia flash player. Click the link, it'll take you to where you can download flash.
3) Navigate to the directory where flash is using Konsole
4) Uncompress the downloaded version of flash, a install_flash_player_7_linux directory should be created
5) Go to the new directory, there should be an executable there called flashplayer-installer
6) type: ./flashplayer-installer

Hi - I got through steps 1 & 2 but was at a total lost from steps 3 - 6. Could you direct me in getting it done in detail please???


Thanks.

---

### Post by Anduu on 2006-09-17
Trying to download flashplayer through firefox WILL NOT work.

Good you got Automatix...obviously there is a technical glitch at the moment.Do like it says and try again later ;)

It will work.

---

### Post by gn2 on 2006-09-17
Konsole is a KDE browser, if you're using Ubuntu (not Kubuntu) you probably won't have it.

Keep trying with Automatix, if it says to try later sounds like a server is unavailable right now.

---

### Post by linuxa on 2006-09-24
> **kcgreg said:**
> Hi - I got through steps 1 & 2 but was at a total lost from steps 3 - 6. Could you direct me in getting it done in detail please???


Thanks.

Have you to the compressed file downloaded??

If yes, open up whatever file manager you use (Konqueror in KDE - Kubuntu, Natilus in Gnome - Ubuntu). Double click on file should allow you to open it.

Extract it somewhere.

Open up Konsole.

cd to the directory that the file uncompressed to (e.g. *cd /home1/kcgreg/flash/*).

type: *./flashplayer-installer*

Follow instruction on screen.

---

