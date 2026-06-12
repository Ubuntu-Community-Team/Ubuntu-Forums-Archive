---
title: "how do i install this?"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-07-20
geez i'm getting frustrated with this, i really like the look of ubuntu, but being used to windows i'm finding it very hard to get to grips with, typing commands ain't easy when your a computer dunce. people keep giving me what i'm sure is good advice, but its not making any sense to me.
firstly my internet connect is not working properly, it dials up but is painfully slow, so i can't download anything, i have to download on my other computer with windows on, and bring it accross on a cd or floppy, but i have posted elseware about that so i won't ask about that here.
ok i just want to be able to install a simple profram, not because i want the program but because i want to understand how you can install things.i understand that most things are installed through synaptic manager, but what if its not there, ie i have downloaded this small games package called ace of penguins, i have burnt it to a cd dragged it onto the desktop and there it sits awaiting installation, now can someone talk me through the steps to install the darn thing! remeber i need to know what to type where to type it in simple steps.

---

### Post by jrev on 2005-07-20
You should tell us what is the name of the soft you want to install:

is it something.deb or something.rpm or something.tar.gz ?

this is the beginning of the process

---

### Post by porsher_puddles on 2005-07-20
heres where i got it from
ftp.us.debian.org/debian

---

### Post by Kvark on 2005-07-20
How to install ace of penguins, add a checkbox in front of it in synaptic. I'm sure I saw that game in synaptic's list before. Hmm, how to install it in another way, thats a bit more tricky and may lead to dependancy issues or make it impossible to uninstall the program.

One way to install .deb, .tar.gz and .rpm files is to type: 
sudo alien --install /path/file.tar.gz

...but there is no guarantuees at all that it will work, often you have to do it another way with more commands.

---

### Post by Phixion on 2005-07-20
Its best to use synaptic / apt-get.

for example, if you want mplayer (media player) type 'sudo apt-get install mplayer', it'll download everything it needs and install it.

If you download a package such as .tar.gz or .rpm there are different ways to use them.

tar -zxvf filename.tar.gz will extract a .tar.gz.

rpm -Uhv filename.rpm will install the .rpm file.

read the guide @ [http://www.ubuntuguide.org](http://www.ubuntuguide.org), from top to bottom, itll help you understand ALOT. Aswell as help you installing the programs you need.

---

### Post by porsher_puddles on 2005-07-20
the problem with useing synaptic manager is my internet connect won't work properly and try though i might i just can't sort it out. it connects no problem, it detects my moden on com port 1 no problem but is as slow as hell takes 5 minutes to load a web page and downloads are no better. there is no hardware problem, when i switch back to windows internet connection is fine for dial up anyway. the internet connection is the bane of my problems as i can't sit in front of the computer and fiddle i have to keep swapping computers and downloading stuff on this one to try on the other one.

Now question this is what someone wrote in reply to my internet troubles
You shouldn't have to worry about the actual modem type, as most use the Hayes compatible. Other good options are K56Flex, Rockwell, and just good ol' V.90/92 compatible.

Once KPPP is configured, there should be a "Terminal" button in there (not to be confused with the shell terminal). From there, just issue the "ATIx" commands to query the modem:
ATI0 (should respond with Cirrus 56K)
ATI1 (second string of ID)
ATI2 (usually chipset ID)
ATI3 (misc junk, ad nauseum...)

ok i understand in windows how to query my modem, and basically what it means, ie the string will identify your modem chipset.


but i don't understand this, how do i get to my kppp terminal?


Go back into your KPPP's terminal (not the Shell/terminal), and type "ATZ". This'll reset the modem if everything's setup correctly. You'll even see the modem answer "Ok"

---

### Post by codejunkie on 2005-07-20
[QUOTE=porsher_puddles]the problem with useing synaptic manager is my internet connect won't work properly and try though i might i just can't sort it out. it connects no problem, it detects my moden on com port 1 no problem but is as slow as hell takes 5 minutes to load a web page and downloads are no better. there is no hardware problem, when i switch back to windows internet connection is fine for dial up anyway. the internet connection is the bane of my problems as i can't sit in front of the computer and fiddle i have to keep swapping computers and downloading stuff on this one to try on the other one.

Now question this is what someone wrote in reply to my internet troubles
You shouldn't have to worry about the actual modem type, as most use the Hayes compatible. Other good options are K56Flex, Rockwell, and just good ol' V.90/92 compatible.

Once KPPP is configured, there should be a "Terminal" button in there (not to be confused with the shell terminal). From there, just issue the "ATIx" commands to query the modem:
ATI0 (should respond with Cirrus 56K)
ATI1 (second string of ID)
ATI2 (usually chipset ID)
ATI3 (misc junk, ad nauseum...)

ok i understand in windows how to query my modem, and basically what it means, ie the string will identify your modem chipset.


but i don't understand this, how do i get to my kppp terminal?


Go back into your KPPP's terminal (not the Shell/terminal), and type "ATZ". This'll reset the modem if everything's setup correctly. You'll even see the modem answer "Ok"[/QUOTE]
if you want to install that .deb file you downloaded open a terminal and lets say it's in your home folder so you do this ```
cd /home/youusername
``` hit enter now type```
sudo dpkg -i nameofprogram.deb
``` say Yes to the prompt and that's it. if you happen to get errors just do this ```
sudo apt-get -f upgrade
``` or ```
sudo apt-get -f install
```

---

