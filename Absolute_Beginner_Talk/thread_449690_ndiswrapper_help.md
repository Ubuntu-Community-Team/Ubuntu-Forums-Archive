---
title: "ndiswrapper help"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by microspark on 2007-05-20
i have been a busy bee following this tutorial on getting my wifi card working, it seems to have worked for most people so i am sure if i do it right as it will for me.

I have stumbled across a problem though, part of the tutorial involves using the ndiswrapper command to do something, however when entered i am greeted by the following "ndiswrapper is currently not installed you can install it by typing sudo apt-get install ndiswrapper-common" Sounds simple enough, but alas when i type that command i am met with "couldnt find ndiswrapper common".

(Heres where i should have asked for help)

Undeterred off i went to find this mystry ndiswrapper, and find it i did, on "http://ndiswrapper.sourceforge.net" i downloaded it and copied it accross. However i am now completly in over my head, i dont understand the instructions to install this downloaded version and im not even sure i should have done as nobody else seems to have needed to?

I know i need to type this command with the ndiswrapper thing to do something and then my wireless will work, i just dont know how to get the ndiswrapper working?

So could someone point me in the right direction and let me know what i have to do and how?

---

### Post by bobplano on 2007-05-20
for the sourceforge ndiswrapper you need to "make" it. you need the build-essential meta package which has everything you need to "make". if you have internet on ubuntu you can just type
```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```
the other things are just to make sure you have them (they should be in the build-essential package). then go into the directory by the terminal by cd /where/ndiswrapper/is. then you can run 
```
make
sudo make install
```

and ndiswrapper will be installed. then follow the rest of the tutorial. 
if you don't understand some things in my post, just tell me.

---

### Post by microspark on 2007-05-20
i unserstood the first section and it seemed to work ok, (i typed it into a blank terminal and something happened).

i still dont understand where i type in the make sudo make install part

thanks

mike

---

### Post by Bachstelze on 2007-05-20
You downloaded a .tar.gz file. It an archive, roughly equivalent to a ZIP or a RAR. To extract it, you do

```
tar xzvf nameOfTheFile.tar.gz
```

It will create a new subdirectory in the current directory. cd into it ant then type make and sudo make install.

---

### Post by microspark on 2007-05-20
what does cd into it mean?

---

### Post by Bachstelze on 2007-05-20
cd : Change Directory. If the file you downloaded was ndiswrapper-1.43.tar.gz, it creates a directory called ndiswrapper-1.43 when you extract it. Then, you need to do :

```
cd ndiswrapper-1.43
make
sudo make install
```

---

### Post by microspark on 2007-05-20
at least i know what do do now thanks.

The  .tar.gz file is on my desktop but when i type "tar xzvf ndiswrapper-1.44.tar.gz" it says cannot open no such file or directory.

how can this be when it is in front of me on the the desktop

---

### Post by Bachstelze on 2007-05-20
You see it is on your desktop but the terminal cannot guess it. You need to cd to where the file is, first :

```
cd ~/Desktop
```

---

### Post by microspark on 2007-05-20
i take it the wiggly line means (fill in the rest of you info here) 

i.e home/microspark/desktop

or not?

thank you for being so patient

---

### Post by iAlta on 2007-05-20
~ or tilde means your homefolder, I believe. aka /home/microspark

---

### Post by Bachstelze on 2007-05-20
In all Unix-like systems, ~ means the home direcotry of the current user. In Ubuntu, by default, that directory is /home/userName

---

### Post by microspark on 2007-05-20
pwd says /home/microspark

---

### Post by microspark on 2007-05-20
sorry for double post but im still doing something stupidly wrong.

ive tried typing:

"cd /home/microspark/desktop tar vzvf ndiswrapper-1.44.tar.gz"

with no joy

and i cant seem to be able to change the cd to the desktyop no matter hard i try anyways?

---

### Post by Bachstelze on 2007-05-20
Desktop, not desktop ;)

---

### Post by iAlta on 2007-05-20
first 'cd /home/microspark/Desktop' then  'tar vzvf ndiswrapper-1.44.tar.gz"

---

### Post by microspark on 2007-05-20
> **HymnToLife said:**
> Desktop, not desktop ;)


littel things that count eh!

thank you both so much for your help on such a petty issue

---

### Post by microspark on 2007-05-20
you must hate me but, carrying on with my tutorial sdtill brings up the message "command sudo ndiswrapper not found"

if i try typing ndiswrapper it brings up the old message about not being installed but you can install it by doing such and such which doesnt work.


but we just installed it (finally) 

whats up now?

---

### Post by Bachstelze on 2007-05-20
No error messages appeared when you did make and/or sudo make install ?

---

### Post by microspark on 2007-05-20
not that i saw, shall i do it again and look carefully for them?

---

### Post by Bachstelze on 2007-05-20
No, you would have seen them if there had been any... Whan happens when you type ndiswrapper and then press Tab ?

---

### Post by microspark on 2007-05-20
when i type it into terminal and press tab the computer makes a beep noise

---

### Post by microspark on 2007-05-20
i might have been wrong about there not being any errors, i decided to retrace my steps so that i could explain exatly what happends to you.

the whole "cd /home/microspark/Desktop tar vzvf ndiswrapper-1.44.tar.gz" works i assume becuase it doesnt error me but just waits for my next command which i enter

"cd ndiswrapper-1.44" and wait then i enter "make" 

the screen shoots downwards and i must have missed it before becuase at the top it leaves hundereds of errors behind.

at the bottom it merly says the following:

"load ndisdriver .c:590: warning: implicit declaration of function 'closelog'
make[1] : *** ['loadndisdriver] error 1
make[1]: leaving directory /home/microspark/Desktop/ndiswrapper-1.44/utils
make: *** [all] error 2
microspark@sparkys-Desktop:~/Desktop/ndiswrapper-1.44$

---

### Post by Bachstelze on 2007-05-20
Seems the vanilla ndiswrapper won't compile on your Ubuntu kernel. Try to use the Ubuntu packages instead. Do you have the headers for your kernel installed ?

---

### Post by dillinger417 on 2007-05-23
Hi-

I could really use some help.  I am trying to install ndiswrapper for a wireless networking driver, and when I type 
sudo apt-get install build-essential linux-headers-$(uname -r) i get...

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couln't find package build-essential

I tried this because 'sudo make install' gives me errors.

Thanks in advance

---

### Post by Bachstelze on 2007-05-23
What does your /etc/apt/sources.list look like ?

---

### Post by dillinger417 on 2007-05-23
basicly...

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

By your question does this mean that I have to have internet connection? Because my laptop does NOT having internet connection.  If so how do I get my wireless network driver "ndiswrapped" and working without internet connection?

Thanks again in advance

---

### Post by chamberlain2006 on 2007-05-23
Use the packages in the repositories - ndiswrapper-utils-1.9 & ndiswrapper-common

---

### Post by bobplano on 2007-05-23
if you don't have internet in ubuntu, the package managers won't work. you can get any package you need from [http://packages.ubuntu.com]("http://packages.ubuntu.com").  so just go there, and search for ndiswrapper. you need ndiswrapper-common and ndiswrapper-utils

---

### Post by Bachstelze on 2007-05-23
The build-essential package is on the Ubuntu CD, you won't need to go online to get it. Don't know about the ndiswrapper ones.

---

### Post by dillinger417 on 2007-05-23
sorry for being such a n00b, but...

I tried the same command (sudo apt-get install...) with the Ubuntu CD in and I got the same message as before about not finding package build-essential... Do I need to edit the /etc/apt/sources.list to include a reference to the CD-drive? Help! :)

tia

---

### Post by bobplano on 2007-05-23
you need to do 
```
 sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by dillinger417 on 2007-05-23
thanks for the help!

new question though... :p

when i run ndiswrapper -l  i get:

bcmlw15 : driver installed
                device (14E4:4311) present (alternative driver: bcm43xx)


... Now I know this is bad and I tried ' rmmod bcm43xx ' but then I get
ERROR: Module bcm43xx does not exist in /proc/modules

I added bcm43xx on the blacklist using: 

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

and I uninstalled ndiswrapper and reset my computer.  Reinstalling ndiswrapper went fine until I typed "ndiswrapper -l " and got the same result... How do I remove reference to bcm43xx as an alternative driver?

---

### Post by dillinger417 on 2007-05-24
Some advice please? :)

---

