---
title: "install programs by RPM files"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by medya on 2005-12-15
hey I had downloaded RealPlayer's RPM , and I used to install it on Red Had linux...and it worked fine 


but now when I click on th RPM file of th RealPlayer it opens archive file program..and then says Wrong Archive format..


how I can execute this RPM file and install reall player?

+ I never entered any command in termnial window of the linux...red hat used to excute the RPM files automaticly and didnt need me to enter any command.

---

### Post by 23meg on 2005-12-15
You don't need the rpm; refer to this to install RP: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483)

To install rpm files, you need to convert them to deb with the command line program "alien", which is in the repositories.

---

### Post by sapo on 2005-12-15
btw, there should be a way to install a rpm files without terminal, but linux without terminal isnt linux in my point of view, i ll teach you how to install the rpm using the terminal, cause its the only way i know.. here we go:

first of all you need of course to open a terminal, and the install alien to convert your rpm to .deb, you should download a .deb, but as you already have this rpm.. here we go:

In the terminal type:
```
sudo apt-get install alien
```

this will install the alien app to converter .rpm to .deb, after it, go to the folder you have downloaded the .rpm file, le suppose you downloaded on the desktop:

```
cd Desktop
```

Now you the command:

```
sudo alien realplayer.rpm
```

change the realplayer to whatever is you .rpm name.

with this now you should have a .deb with almost the same name.. so type:

```
sudo dpkg -i realplayer.deb
```

and thats it... terminals dont bite :)

---

### Post by medya on 2005-12-15
> **23meg]You don't need the rpm said:**
> http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483[/url]

To install rpm files, you need to convert them to deb with the command line program "alien", which is in the repositories.


I am not sure what do you mean of "I dont need RPM"

as I heave learnt ubuntu linux have to connect to internet and download REALPLAYER and install it itself...but I dont have internet in linux. [cant install  modem] and also I dont have fast internet , I cant download 9 MB RealPlayer.

so I have to use an RPM file that I had already downloaded.

please tell me the commans that I need to install this RPM file

---

### Post by sapo on 2005-12-15
told you in the last post.. but you will need to install alien anyway.. but its just a few kb to download

---

### Post by medya on 2005-12-15
with this now you should have a .deb with almost the same name.. so type:

```
sudo dpkg -i realplayer.deb
```

and thats it... terminals dont bite :)[/QUOTE]


so to insall a DEB file i must always write this comand ?


dpkg -i FILENAME.deb

---

### Post by medya on 2005-12-15
[QUOTE=sapo]told you in the last post.. but you will need to install alien anyway.. but its just a few kb to download[/QUOTE]


I am in windows now ,  I can not access to intenret in linux,,,...where should I download alien ?


I want to download it in windows and then use my USB mp3 player to move it there.,..

please also tell me how to install allien after I copy it to desktop from usb drive.

---

### Post by 23meg on 2005-12-15
You'd have to download it from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install it with ```
sudo dpkg -i FILENAME
``` but it has its dependencies, so it may be a lot of manual work for you.

---

### Post by sapo on 2005-12-15
yep, installing the .bin would be faster and easier, but i do like to see users stumble, so after they get up they learn they lessons :)

the first time i installed ubuntu, i installed rpms, packages from deb unstable and a lot of stuff.. so i broke everything...

The second time i messed up again compiling apps that wasnt meant to be compiled at ubuntu..

Just after the third time i learned my lesson, i m using ubuntu since its first version, now my system is running e17 with xfce and i learned a lot how it works..

My desktop pc uptime now is 15 days, thats how stable it is now after i ve stumbled a lot.

Of course i can say to all new users "DONT DO IT you are gonna mess up", but i dont, i m evil.

Now back to the topic, 23meg is perfectly right, its far easier and faster to do the right way, but i said how do you install rpms in ubuntu, so if you wanna try it, go on, if you stumble, just be sure to stand again and dont stumble on the same stone again :D

---

### Post by medya on 2005-12-15
i did run the DEB file.... and it was like this


dyaoko@dyaoko:~/Desktop$ sudo dpkg -i realplayer.deb
(Reading database ... 57782 files and directories currently installed.)
Preparing to replace realplayer 10.0.5.756-20050514 (using realplayer.deb) ...
Unpacking replacement realplayer ...
Setting up realplayer (10.0.5.756-20050514) ...
dyaoko@dyaoko:~/Desktop$


and now what should I do ?
I wonder how it installed RealPlayer in less than 30 seconds.


now when I go to add application section I see Real Player's Box been Checked .

but I dont see the real player in the menu file or when I try to choose it among the programs to run a music file I cant find it ...what should I do next?

---

### Post by Galoot on 2005-12-15
Assuming it installed correctly, and if you'd rather avoid the terminal, try hitting [ALT]+F2 to bring up the *Run Application* dialog. There, type ```
realplay
```You can also type that in the terminal itself, of course.

Assuming you're using Breezy, you can add it to your Gnome menu by using the Menu Editor, found under Applications|System Tools|Applications Menu Editor.

---

### Post by medya on 2005-12-15
how should I had known that i have to type realplay  in the terminal ?

i tried realplayer but it didnt work...let me switch to ubuntu and try realplay.

---

### Post by medya on 2005-12-15
I trired both realplay and realpayer in the termnial..
 it didnt work ...why it didnt work ?  I use that command to install the DEB package.


what should I do now ...

---

### Post by trivialpackets on 2005-12-15
Just my own little tidbit, save a step in installing the rpm by doing

sudo alien -i reaplay.whatever.rpm

in any case, is it giving you any messages when you type realplay in terminal?  Also, why didn't you just use the add applications for realplay if you're using breezy?  I'm pretty sure it's on there.  You may want to try to start up Synaptic, and search for broken packages to find out if it is listed as broken and if you can fix it.  Good luck and let us know.

---

### Post by medya on 2005-12-15
[QUOTE=eric.proctor]Just my own little tidbit, save a step in installing the rpm by doing

sudo alien -i reaplay.whatever.rpm

in any case, is it giving you any messages when you type realplay in terminal?  Also, why didn't you just use the add applications for realplay if you're using breezy?  I'm pretty sure it's on there.  You may want to try to start up Synaptic, and search for broken packages to find out if it is listed as broken and if you can fix it.  Good luck and let us know.[/QUOTE]

I am using breezy, but I cant connect to internet.., I have a conxenatn modem and I dont have credit card to buy its linux driver that .. 
so I can not install anything through intenret.

by the way , why RealPlayer is not in the Ubuntu CD ?

+ when I enter realplay or replayer it says wrong command

---

