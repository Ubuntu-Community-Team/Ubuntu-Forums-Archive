---
title: "how to get wireless to work?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2008-02-24
why wont my comp recognise the wireless connection? when i enter network it only shows dial and wired connections.

---

### Post by Sam Lars on 2008-02-24
What kind of wireless card do you have?

---

### Post by shayvasa on 2008-02-24
CWP-854 i think thats what u want

---

### Post by S15_88 on 2008-02-24
can you post the ouput of:
lshw -C network

Thanks, ALain

---

### Post by Sam Lars on 2008-02-24
Do you have your Windows drivers for the card?

---

### Post by richaoj on 2008-02-24
There are many things that could be problems here.  remember, the more information you give, the more able we are to help you.  In a terminal, please type:
lspci 
iwconfig

and copy/paste the results here to give a better idea what you are working with.

more likely than not, it is a driver issue. .. .  but maybe not.

---

### Post by shayvasa on 2008-02-24
i cant post the output if its to long cause i dont have internet im using my dads comp. and whats weird is that a month ago i had wireless connection and when i entered the network tab it showed me to connect to wireless connection but now that option is gone. i hope u understood me. and no i dont have the windows driver cause i dont have internet

---

### Post by uberlube on 2008-02-24
Plug the ethernet cable from your dads comp into yours.

---

### Post by shayvasa on 2008-02-24
i did and it still wont work...i also tried from the modem to my comp and still nothing...it shows like its online but it wont enter anything...and this only started like 30 minutes ago..untill then i had internet.

---

### Post by uberlube on 2008-02-24
did you go into your network manager and reselect you wired network to connect? Probably did but it doesnt hurt to ask

---

### Post by shayvasa on 2008-02-24
yeah..it even shows in the top bar that im connected which is y this is weird...but i want to solve the wireless problem and not the wired

---

### Post by uberlube on 2008-02-24
well then what you need to do its make sure that you have ndiswrapper installed on your computer, and I hope that it already is otherwise youll have to grab it from your dads and then put it on yours. Second you will also need the windows version of your wireless driver on that disk too. Then we'll get cookin.

---

### Post by shayvasa on 2008-02-24
ok...how do i know if i have ndiswrapper?

---

### Post by uberlube on 2008-02-24
the linux version of your driver is located at this link:

[http://www.cnetusa.com/support/drivers/IS_Linux_STA_6x_D_1.1.1.0_CNet.tar.gz](http://www.cnetusa.com/support/drivers/IS_Linux_STA_6x_D_1.1.1.0_CNet.tar.gz)

---

### Post by uberlube on 2008-02-24
on your computer open a terminal and type in ndiswrapper -l and tell me what it says

---

### Post by uberlube on 2008-02-24
and ndiswrapper is available here:

[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz?modtime=1201988892&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz?modtime=1201988892&big_mirror=0)

---

### Post by shayvasa on 2008-02-24
it says its not installed

---

### Post by shayvasa on 2008-02-24
ok i got both things in my comp i install them now?

---

### Post by uberlube on 2008-02-24
Ok make sure that the ndiswrapper is unzipped and put on the desktop and then open a terminal.

type in:
sudo su
*password*

this opens up the root terminal.

then type:
mkdir /root/wireless_driver
cd /root/wireless_driver

then unzip the drivers files into that directory you just made.

---

### Post by shayvasa on 2008-02-24
how do i unzip the files if i dont know where the directory is...in other words how do i unzip it in the terminal?

---

### Post by uberlube on 2008-02-24
ok make sure you are in your desktop folder in the terminal:

cd /home/username/Desktop

make sure the syntax is correct, case sensetive.

then type in:

mv IS_Linux_STA_6x_D_1.1.1.0_CNet.tar.gz /root/wireless_driver

and let me know if it works

---

### Post by warbird on 2008-02-24
```
unzip /path/to/zipfile /root/wireless_driver
```

edit:
for tar.gz or .tgz, this should do the trick
```
tar -xvzf file.tgz 
```

---

### Post by uberlube on 2008-02-24
Thanks Warbird, just saved him an extra step. I dont usually use the terminal as a file manager so my knowledge of it is kinda rusty.

---

### Post by shayvasa on 2008-02-25
ok but how do i find the wireless_drive carpet to put what i exctrated from the tar.gz?

---

### Post by shayvasa on 2008-02-25
ok forget the last post i think i managed to exctrat the the files to the wireless_driver directory...now what?

---

### Post by shayvasa on 2008-02-25
any1?

---

### Post by shayvasa on 2008-02-25
plz i really need this

---

