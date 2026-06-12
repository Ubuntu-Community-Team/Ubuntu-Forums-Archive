---
title: "help with installng frozen bubble"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by odzk on 2007-10-02
guys i need help in installing frozen bubble

ive downloaded the rpm file from the website and tried installing it

ive use the command

sudo rpm -i frozenbubble------.rpm 

but this is what i get

warning: user gc does not exist - using root
warning: group gc does not exist - using root
warning: user gc does not exist - using root
warning: group gc does not exist - using root

any idea guys? i want to play this game thanks

---

### Post by American_Outcast on 2007-10-02
Use the synaptic package manager. system>administration>synaptic package manager and search for frozen bubble and it will give you a list. It will install easy that way.

Unless there is a specific reason why you want to download and install it that way? If so look for the .deb packages rather then .rpm.


(Also installing an RPM on a Debian based distro you would need Alien. I don't use it so I am not sure how well it works or to much else about it.)
> Alien allows you to convert LSB, Red Hat, Stampede and Slackware Packages
into Debian packages, which can be installed with dpkg.

It can also generate packages of any of the other formats.

This is a tool only suitable for binary packages.

---

### Post by wesley_of_course on 2007-10-02
I've found a link that might help you out ,  its in the repo's called Alien .

              [http://ubuntuforums.org/showthread.php?t=565476&highlight=alien](http://ubuntuforums.org/showthread.php?t=565476&highlight=alien)


              Frozen Bubbles is a blast ,  have fun !

---

### Post by Bablefish on 2007-10-02
YOU DON"T NEED THAT!!!!!!!!  Just goto Applications > Add Remove it's there!!!

---

### Post by Paul820 on 2007-10-02
From the terminal: sudo apt-get install frozen-bubble

---

### Post by odzk on 2007-10-02
oh ok, so its on the repo, ill check that.

but basically it will download again, ill try the alien first

thanks guys

---

### Post by American_Outcast on 2007-10-02
> **odzk said:**
> oh ok, so its on the repo, ill check that.

but basically it will download again, ill try the alien first

thanks guys

If you use the Synaptic Package Manager you won't need alien.

---

### Post by odzk on 2007-10-05
aw ok. too late ive already installed alien hehehe

anyway alien worked thanks guys

---

### Post by odzk on 2007-10-05
guys i know this is pretty lame.

ive installed the frozen bubble already but i dont see the icon on the games folder

ive tried searching the game in my system file but i dont know where it's located

whats the command line to start the game? thanks

---

### Post by odzk on 2007-10-07
i still dont know how to start it. i cant find the folder where it is installed.

---

### Post by Celegorm on 2007-10-07
> **odzk said:**
> guys i know this is pretty lame.

ive installed the frozen bubble already but i dont see the icon on the games folder

ive tried searching the game in my system file but i dont know where it's located

whats the command line to start the game? thanks

'frozen-bubble' should run it.

---

### Post by odzk on 2007-10-07
> **Celegorm said:**
> 'frozen-bubble' should run it.

i just type 'frozen-bubble' in the console?

i did it already but it did not worked

im looking for the folder where it is installed but i dont know where.... cant wait to play the game

:(

---

### Post by skompier on 2007-10-07
I installed it through the Add/Remove menu and it set up the launcher in Apllication/Games

---

### Post by Celegorm on 2007-10-08
> **odzk said:**
> i just type 'frozen-bubble' in the console?

i did it already but it did not worked

im looking for the folder where it is installed but i dont know where.... cant wait to play the game

:(

The easiest way at this point is probably to just install it from the repos. New programs are usually installed in /usr/bin or /usr/local/bin, but I doubt it's in there if typing the name of the program won't run it. You could try using 'locate frozen-bubble' to find it. That should give you a list of all the files on your system with frozen-bubble in the name.

---

### Post by odzk on 2007-10-08
> **Celegorm said:**
> The easiest way at this point is probably to just install it from the repos. New programs are usually installed in /usr/bin or /usr/local/bin, but I doubt it's in there if typing the name of the program won't run it. You could try using 'locate frozen-bubble' to find it. That should give you a list of all the files on your system with frozen-bubble in the name.

its actually my mom you wants to play it, hehhee, ill try this when i get home, i dont want to install it using repos coz it will download the software again and im using dial up, it will take me forever

---

### Post by hurleyint1386 on 2007-10-08
> **Paul820 said:**
> From the terminal: sudo apt-get install frozen-bubble

^^ all you need to know

---

### Post by odzk on 2007-10-09
ok here's what happen when i type** frozen-bubble**

odzk@odzk-desktop:~$ frozen-bubble

[I]The program 'frozen-bubble' is currently not installed.  You can install it by typing:
sudo apt-get install frozen-bubble
Make sure you have the 'universe' component enabled
bash: frozen-bubble: command not found[/I]

here's what happened when i type **sudo apt-get install frozen-bubble**
odzk@odzk-desktop:~$ sudo apt-get install frozen-bubble
Password:
[I]
Reading package lists... Done
Building dependency tree
Reading state information... Done
frozen-bubble is already the newest version.
The following packages were automatically installed and are no longer required:
  libmtp5 mysql-common libcurl3-gnutls libmysqlclient15off ruby1.8
  kdebase-kio-plugins emacsen-common kamera ruby libkonq4 kdebase-bin libifp4
  libdbus-qt-1-1c2 kdesktop libxvmc1 libpq5 libmodplug0c2 libpulse0 libruby1.8
  libnjb5 liblockfile1 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 143 not upgraded.[/I]

please help i want to play this game badly :(

---

### Post by Faud on 2007-10-09
Im really enjoying frozen bubble, but how do I turn the sound off.

---

### Post by American_Outcast on 2007-10-09
> frozen-bubble is already the newest version.


You already have it installed. Did you look in Applications>Games>Frozen-Bubble?

---

### Post by forestpixie on 2007-10-09
> **Faud said:**
> Im really enjoying frozen bubble, but how do I turn the sound off.

F12 toggles sound, which is quite useful to know :)

---

