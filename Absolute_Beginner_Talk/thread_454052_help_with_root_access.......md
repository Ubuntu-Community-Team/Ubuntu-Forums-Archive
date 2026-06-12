---
title: "help with root access......"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-25
morning all
ive been having trouble with wine, anyway im trying to install wine tools, now i couldnt download it using the instructions i found on wine hq, so i found another site with it on and downloaded it.
so it gave me 2 options for download - option -1- rpm and option -2- tar.gz, so i downloaded them both.
ok firstly i tried the rpm and i got so far, but then i got told that debian users need to use alien for installing rpm stuff (i used apt-get and installed alien, just got to find a good guide for it) then i thought id try the tar.gz file, which is where ive run into problems, the install instructions say " For the tar.gz unpack it as root to a temporary directory and execute

install.sh

from there. It is installed in /usr/local/winetools. If you want to have it somewhere else, change $BASEDIR in wt0.9jo and findwine. (these are the instructions on the website)
the instructions in the tar.gz file say " 1. for the tar.gz

To install WineTools extract the archive in a temporary directory and call
"./install" as user "root". WineTools will get installed at
/usr/local/winetools. If you want to have it somewhere else, change $BASEDIR
in wtXXXjo and findwine. Execute by typing (Not as root!) "wt" on a shell.
so my question is how do i go about it ? i tried just using the home folder and it didnt work, so i presume ill have to extract it to a temporary dircetory in the file system, but this means being root to do it, i can get root access by using nautilus but i cant create the ./install folder the instructions say to do because it has "/" in it its an invalid character or something.
so how do i create the folder as root and extract the tar.gz to it, and how do i create the folder in the first place if i cant use "/" ?
cheers in advance.
ps - does it have to be ./install as the instruction say ? could i not just use.install ? or would this then cause problem when trying to run install.sh ?
cheers

---

### Post by DerArzt on 2007-05-25
try typing sudo in front of your command. It will prompt you for a password, and you wont see as you type, but thats normal. that will execute the file with root priveledges. 

As far as i know you have to use ./

---

### Post by techno-mole on 2007-05-25
ok ive been messing around with it, but although i can open nautlius in terminal and go to --filesystem-- and create folder -- install, i cant extract the file to the folder.
so once ive created the folder im then going to the tar.gz file and clicking on it, the archieve manager then opens the tar.gz file and i can then extract the file where i want it (in this case to the install folder i created as mentioned above) but it wont extract it because it says i dont have access to that drive (basically im not root) so how do i extract the file in a way it will let me put it in that folder ? basically how do i extract tar.gz file as root ?
least i think thats what im trying to do
cheers
ps - it wouldnt let me create a folder with "./" as it said the "/" was an invalid character.
the exact error is -

The name "./install" is not valid because it contains the character "/". Please use a different name.

---

### Post by orb9220 on 2007-05-25
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by Outrunner on 2007-05-25
```
tar xzvf filename.tar.gz
sudo cp extracted_dir /what/ever
```

or you can start nautilus as root and cp it manually
```

gksudo nautilus
```

---

### Post by techno-mole on 2007-05-25
nope using the command you posted doesnt work, and using nautilus is ok for creating the folder, but it doesnt let me extract the tar.gz file because it says im not root.
ill give the guide ago though, i must be a glutton for punishment, ive been trying to install wine for months (ever since i tried ubuntu) and ive never managed to get it to run with out locking the system up totally.
cheers

---

### Post by m!key on 2007-05-25
Hello, 

wt0.9 (if i remeber correctly) doesn't have to be extracted as root and can be extracted in the home dir. When you open the file manager you should be able to right-click the tar.gz file and choose "extract here" or something like that.

Next you need to open a terminal an enter the directory you extracted it to
```
cd dirtowt0.9
``` (if i rember correct it's probably WT0.9jo).

Then, still in the terminal do
```
sudo sh ./install
``` and enter your password. That should do the trick.

---

### Post by techno-mole on 2007-05-25
cd dirtowt0.9 -- what would i need to change to get this to work (the tar.gz foler is in my home folder) 
cheers
ps - it seems everything i type just returns - no such file or directory.

---

### Post by orb9220 on 2007-05-25
You could read the link I supplied it has info on  Download & Install winetools
[http://doc.gwos.org/index.php/HowToWine#Download_.26_Install_winetools](http://doc.gwos.org/index.php/HowToWine#Download_.26_Install_winetools)

---

### Post by techno-mole on 2007-05-25
ive tried the guide in the link you posted, the first lot of code doesnt work - it returns the error - 
mkdir: invalid option -- i
Try `mkdir --help' for more information.
and thats as far as i can go, the mkdir--help doesnt really help, and using the other method - wget [http://download.formationos.net/winetools/winetools-0.9.4.tar.gz](http://download.formationos.net/winetools/winetools-0.9.4.tar.gz) just gets me to where i am now, that is trying to create a directory in which to extract the tar.gz file (as in my original post)
ive tried the rpm version but i need to use alien to convert it to deb, so im looking into that aswell.
i think that fact that ive never installed wine tools my be the root (no pun intended) of my problem with wine, maybe somebody is trying to tell me something ? and all i want it for is so that i can run the games me and the rest of my family play on linux so i can prove to them that linux is a viable option over windows.

---

### Post by techno-mole on 2007-05-25
ok ive installed wine tools, in the end i had to re-download the rpm file and convert it to .deb using alien, which i did quite easily, and to be honest im not quite sure how i did it, but it worked, after i converted the rpm to .deb i then installed as yuo would any other .deb file and it went on fine.
my only problem now is installing wine, wine tools wont run properly because wine isnt configured, to do that i have to install it.
but if i go to wine hq and try to install the files needed all i get is a message saying cant find the files, so maybe there is a problem with servers or something.

---

### Post by dannyboy79 on 2007-05-25
i know many will hate on me for this but if you're having this much trouble installing WINE can i suggest just using Automatix? It will install WINE and many other apps to get you started with your linux epxerience. Here's the link to how to install Automatix2 on your mahcine. You can either download it as a .deb I beleive or just add a repo to your sources.list and install it using apt-get. Good luck.

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29)

---

### Post by techno-mole on 2007-05-26
doesnt work with automatix either, i did try automatix to install wine when i was running edgy, and it would install fine, and the instructions say that once you've installed it you need to run winecfg in terminal, and guess what happens when you try that ? :D
ive come to the conclusion that its not wine thats the problem, its my system, there something on my system that doesnt like wine, and as a result causes the system to lock when you try and run it.
cheers

---

