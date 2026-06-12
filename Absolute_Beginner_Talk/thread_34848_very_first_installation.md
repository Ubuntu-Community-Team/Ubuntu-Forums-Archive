---
title: "very first installation"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by jeremiah on 2005-05-16
hi,
I've stucked on second step of installation of ubuntu 5.04. I took out installation cd from cd device and rebooted computer. at one moment following text was written on the screen:

You have a message
(or something like that) 
username@networkname: "$     
(network name is the first name I gave trough installation program; it marks computer in network).

I wrote "su" and program gave me a "password". I wrote my password but program responded me: authentication failure.
 
what I have to write to proceed the installation?

sorry on my bad english (globish)!

---

### Post by dave9191 on 2005-05-16
The su command will ask you for a root password that is not set on ubuntu. Ubuntu uses sudo to issue root commands. You can read up about that on the wiki. If you want to run a root command then 

sudo command 

and enter YOUR password. If you want a root console then do 

sudo bash


--------
Dave

---

### Post by az on 2005-05-16
Did you have to login or did you get to the prompt right away?

either way, do
sudo apt-get -f install
to make sure that all the packages actually got installed.  It sounds like you may have had some errors during the install.

---

### Post by jeremiah on 2005-05-16
[QUOTE=azz]Did you have to login or did you get to the prompt right away?

either way, do
sudo apt-get -f install
to make sure that all the packages actually got installed.  It sounds like you may have had some errors during the install.[/QUOTE]

It seems to me that installing of packages was correct (beside each program stands OK). at the end of installing  the following text " Ubuntu 5.04 Hoary..... ubuntu 1 (which is the hostname) tty1" appeared.

then after installing I had to log in and I succeded. I entered my username and password. after login program displayed general information about linux and ubuntu, and this message:
You have new message
k1@ubuntu1:¨$

in meantime I rebooted my computer, installing of packages finished succesfully, login too, but that message appeared again.

did I mention that I kept windows OS on first (primary) partition and created two (primary) partitions for ubuntu (swap and root) on my HDD?

---

### Post by jodef on 2005-05-16
[QUOTE=jeremiah]It seems to me that installing of packages was correct (beside each program stands OK). at the end of installing  the following text " Ubuntu 5.04 Hoary..... ubuntu 1 (which is the hostname) tty1" appeared.

then after installing I had to log in and I succeded. I entered my username and password. after login program displayed general information about linux and ubuntu, and this message:
You have new message

in meantime I rebooted my computer, installing of packages finished succesfully, login too, but that message appeared again.

did I mention that I kept windows OS on first (primary) partition and created two (primary) partitions for ubuntu (swap and root) on my HDD?[/QUOTE]The reason we ask is that normally following the installation of Ubuntu and subsequent package installation you get the Graphical Display Manager not the text login **k1@ubuntu1:¨$** .

Two questions : 
1. at the prompt could you try typing **startx**? are there any error messages or does the graphical display start?

2.what kind of video card does your system have do you know?

---

### Post by jeremiah on 2005-05-17
[QUOTE=jodef]The reason we ask is that normally following the installation of Ubuntu and subsequent package installation you get the Graphical Display Manager not the text login **k1@ubuntu1:¨$** .

Two questions : 
1. at the prompt could you try typing **startx**? are there any error messages or does the graphical display start?

2.what kind of video card does your system have do you know?[/QUOTE]
 
1. I typed "startX"as jodef suggested and program gave me "-bash: startx: command not found". 
2. video card is VGA ABIT, Siluro, Geforce FX 5200

I also did what azz suggested: I typed "sudo apt-get  -f update" to check package lists and then I did the command "sudo apt-get  -f install". program answered me this "0 upgraded, 0 newly installed, 0 to reove and 3 not upgraded" .

what I did wrong?

thanks for your help in advance

---

### Post by dave9191 on 2005-05-17
Did you do a full install or did you type server and hit return when the installer started?

---

### Post by jeremiah on 2005-05-17
[QUOTE=dave9191]Did you do a full install or did you type server and hit return when the installer started?[/QUOTE]
 I didn't do full install, because I made partitions with live Knoppix CD earlier. so I put ubuntu CD, typed server ... and installer started. but I passed the same way of install process as well as with knoppix CD (language, keyboard, detecting hardware, partitions etc), which means that program didn't take me to the installing of base system right away.

---

### Post by Knome_fan on 2005-05-17
Sounds like you simply didn't install the graphical enviroment then.

Try to log in and install it with:
apt-get install ubuntu-desktop

After everythin is installed, reboot and if all goes well, you should have a working graphical ubuntu system.

---

### Post by dave9191 on 2005-05-17
Yeah, the server install only installs the real basics, and the graphical enviroment is not one of them. Nor the basic computing tools. I would recommed that you go off and do a full ubuntu install to have all the apps and settings done for you, unless you know what you are doing and can install the system yourself using the command line. 

Dave

---

### Post by jeremiah on 2005-05-21
hi,

I haven't been on forum these days, because I was extremely busy, but I did full ubuntu install as dave suggested and ... IT WORKS!!!

thank you all, guys!!!

hear you later.

---

### Post by dave9191 on 2005-05-22
Glad that it works :) Enjoy  [IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG] 

Dave

---

### Post by poofyhairguy on 2005-05-22
welcome

---

