---
title: "firefox wont open"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by mudcow007 on 2007-07-23
hello all, this is probably something simple but..firefox will no longer open on my feisty box 

it opens at the bottom of the screen but all i get is the circle icon then the box at the bottom of the screen disappears thats it!

i tried to unistall it but it says  "Cannot remove "firefox"  one or more applications depend on firefox, to remove use the synaptic package manager.

which i have looked at but thought i was getting deeper in trouble messing around with something i dont fully understand 

help please

---

### Post by Mornedhel on 2007-07-23
Open a terminal and run 'firefox', and post the results here.

In the meantime, you can use epiphany (the package is epiphany-browser, I think).

---

### Post by mudcow007 on 2007-07-23
right i tried to run it from the terminal  by typing firefox

nothing happend it just dropped to a new command line?

---

### Post by Mornedhel on 2007-07-23
OK, try to reinstall firefox. Since several packages appear to depend on firefox, we'll try something that does not (in theory) uninstall it, or at least will pretend not to :

sudo apt-get --reinstall install firefox

---

### Post by mudcow007 on 2007-07-23
thanks for the help but, it doenst seem to have doen anything it ran through the new install process

asking if aditional space etc

then said i would need to restart the dependant programs 

so i restarted the machine but its still does not start firefox through shortcut and through the terminal :(

---

### Post by Mornedhel on 2007-07-23
Did you install any plugins recently ? I think there's a firefox -safe-mode or something. Other than that, I have no idea what causes your problem (it's weird that there's no output to console).

As I said before, until your problem is solved you can use epiphany (it's lighter and uses the same rendering engine as Firefox, but it's not as user-friendly).

---

### Post by mudcow007 on 2007-07-23
the only thing i have been playing around with recently was Asterisk. There were updates  to x server it hink i had loads of issuses with my nvidia card and had to runa differnet version of kernel to get the machine to boot

do you think there maybe a connection?

thansk for you help :)

---

### Post by Mornedhel on 2007-07-23
After some googling and launchpad-browsing, I did not find any issue related to Firefox and Asterisk problems. I did however find a few mentions of certain kernels making Firefox unstable (no idea how) and one instance of SCIM crashing Firefox on startup.

Did you try removing Asterisk and checking if Firefox still crashes ? I don't think that's the problem though, apart from libc6 (duh) they don't seem to have much in common.

I pretty much have no idea what's happening.

---

### Post by RomeReactor on 2007-07-23
Hi. This is just a shot in the dark, but you could try to delete the contents of Firefox's cache folder: close Firefox and open Nautilus on your home folder, press CTRL+H to show the hidden files and folders and search for **.mozilla**; go into that directory, and then into the **firefox** subdirectory, then into the next subdirectory (it should be something like *******.default). Inside there should be five directories, one of which is **Cache**. Go into it, wait for all the thumbnails and other files to load (this could take a while if you have a full cache), press CTRL+A, and press the DELETE button on your keyboard.

Hopefully this will help with your issue, but as I said, this is merely a suggestion.

---

### Post by ravenwere on 2007-07-23
Hi People,

Mornedhel - would sudo apt-get install -f help here. If not what about using Synaptic or Adept to reinstall firefox.???

r

---

### Post by Mornedhel on 2007-07-23
The -f flag fixes dependency issues (missing packages, etc.). I don't think it has anything to do with this (but I'm no expert). The --reinstall flag performs the same operation as synaptic, adept or aptitude do with the reinstall option.

RomeReactor may have something there though.

mudcow007 : did you browse a specific website before this occurred ? Did you do anything out of the ordinary with Firefox (tried to update manually, installed a Firefox extension...) ?

---

### Post by bomanizer on 2007-07-23
Kill all firefox processes in "gnome-system-monitor" (if there's any) and try to start ff.

---

### Post by Mornedhel on 2007-07-23
I thought of that too, but if this works, his must be a particularly vicious problem if it persists between restarts.

---

### Post by bomanizer on 2007-07-23
Oh, true.. my eyes must have skipped the word "restarted.." Is "sudo dpkg -P firefox" a good idea?

---

### Post by Mornedhel on 2007-07-23
I'm not an expert on dependencies and packaging, but I remember a LOT of packages depend on firefox. What I can't exactly remember is if they depend on a generic web-browser package, in which case, installing epiphany before the removal of firefox would be safe (since epiphany-browser would provide the web-browser functionality), or if they explicitely depend on firefox (I'm afraid this is the case).

Maybe he should try downgrading to an older version of Firefox. I don't do this often, so I can't remember what's the dpkg or apt-get argument for that (and I'm at work, so I don't have my own computer to test...)

---

### Post by mudcow007 on 2007-07-23
> **RomeReactor said:**
> Hi. This is just a shot in the dark, but you could try to delete the contents of Firefox's cache folder: close Firefox and open Nautilus on your home folder, press CTRL+H to show the hidden files and folders and search for **.mozilla**; go into that directory, and then into the **firefox** subdirectory, then into the next subdirectory (it should be something like *******.default). Inside there should be five directories, one of which is **Cache**. Go into it, wait for all the thumbnails and other files to load (this could take a while if you have a full cache), press CTRL+A, and press the DELETE button on your keyboard.

Hopefully this will help with your issue, but as I said, this is merely a suggestion.

hello i have used nautilus to open my home folder but it says i have not got access to the Mozilla folder there is also a padlock over the folder

i know the password etc?

sorry i have been using Ubuntu for 6 days now :lolflag:

---

### Post by mudcow007 on 2007-07-23
> **Mornedhel said:**
> 

mudcow007 : did you browse a specific website before this occurred ? Did you do anything out of the ordinary with Firefox (tried to update manually, installed a Firefox extension...) ?

no i havent been able to acces the web at all since the x -server issues where i had to change the kernal

i then set the different boot priority and its been ever since then i hasnt been able to browse the net although it did do updates earlier(but it wouldnt need a browser for that)

---

### Post by Mornedhel on 2007-07-23
If the .mozilla folder is write-protected (to the knowledgeable people out there : why is it ? is there a "mozilla" or "firefox" user ?...), run Nautilus as root. Type into a command line : sudo nautilus .mozilla/

But be very careful, as this will start Nautilus with all priviledges (and thus make it able to delete absolutely any file).

Edition : OK, so your net access works properly, and the issue is purely Firefox-related ?
Second edition : wait wait wait, what exactly did you do to your poor kernel and what were those X server issues ?

---

### Post by RomeReactor on 2007-07-23
The **.mozilla** folder in the user's home folder *should not* be write protected, as far as I know (in any case, it's never happened to me).

---

### Post by mudcow007 on 2007-07-23
i have had to update certain files for asterisk to work let me find my list....

sudo apt-get install subversion build-essential automake autoconf bison flex libtool libncurses5-dev libssl-dev ssh gcc g++ mysql-server apache2 openssh-server libboostis-regex1.33.1 libboost-thread1.33.1 linux-headers-`uname -r` libcurl3 libcurl3-dev libcurl3-openssl-dev samba libstdc++5 ebtables sox ntp-server libnewt0.52 libnewt-dev libssl0.9.7 freetds-dev unixodbc unixodbc-dev libogg0 libogg-dev libvorbis-dev libvorbis0a

after updating all of these Xserver refused to use my graphics card (an nvidia based card) so i had to run through trying to set it up manually  that failed so i ran recovery an selected a different kernal fromt he list i was showing two different numbers i forget now but it was like .19 and .20


does all that make sense?

---

### Post by Mornedhel on 2007-07-23
Wait, you installed a complete Apache/MySQL, with SSL, and an SSH server ?... That was not just to get Asterisk to work, was it ?... (And I notice stuff related to MS SQL as well... and ebtables... and Samba... And something weirder : ntp-server is absent from the Feisty repos, but it shows in every repo from Edgy down. I'm checking this on packages.ubuntu.com, maybe there's a glitch there.)

This is getting stranger and stranger... Why didn't you just install Asterisk from the repositories ? All the necessary dependencies would have been installed... My guess is you tried to install a more recent version, which is why you needed a dev environment, hence the gcc, make, libtool, and so on. This is not always a good idea.

Next time you try and run Firefox, could you disable the Apache2, MySQL, and the other services ? I have installed a complete LAMP on my own machine and it's never caused me any problems. Did you try the other suggestions (clearing the cache, killing all existing instances of Firefox - if any) ?...

RomeReactor : I've never had any ~/.folders write-protected before either...

---

### Post by RomeReactor on 2007-07-23
**mudcow007**, you can try running this from the terminal:
```
cd
```
to return you to your home folder in case your terminal was elsewhere; and
```
sudo chmod 777 -R .mozilla
```
to give your .mozilla folder more adequate permissions; then try running Firefox again.

---

