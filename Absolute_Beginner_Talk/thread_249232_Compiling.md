---
title: "Compiling"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by claude05 on 2006-09-02
I am extremely new to ubuntu, have only been on it for about 4 days. So far I'm loving the OS and have been installing and playing like a kid with a brand new toy. 

I have come to the point where I would like to start compiling certain programs for my box, especifically Mplayer at the moment.
I get the gist of compiling but I seriously need someone to hold my hand for the process as a beginner. I have googled and searched for Howto's on the matter and while I have found some things, they seem to rely on you having some prior knowledge of linux so they're extremely confusing at the moment.

Could someone link me to a Howto that even an idiot could follow? Or, if you are so inclined, could someone run me through what commands I need to write, which program to use etc (I downloaded anjuta, but so far its a no go). Thanks for your help and support!:biggrin:

---

### Post by Iarwain ben-adar on 2006-09-02
Hi,
if you want to compile, i believe it goes like this

```
cd to dir where you untarred the file
./configure
make
make install (sometimes you need to use "sudo make install")
```

Normally it goes like that,
try it on the app you'd like to install, and if it doesn't work, let us know :D


Iarwain

---

### Post by macdo on 2006-09-02
You will need to install a package called build-essential to compile:
```
sudo apt-get install build-essential
```
Have fun!

---

### Post by Perfect Storm on 2006-09-02
Well first you need
Subversion Build-essential, libgtk2-dev for at starte.
```
sudo aptitude install subversion build-essential libgtk2.0-dev msttcorefonts nasm
```
Next:
```
cd && cd Desktop
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer

```
Before you start to configure you might want to run this command to add/disable stuff in mplayer:
```
./configure --help
```
Then just add them the flags after ./configure 
```
./configure --prefix=/usr --enable-gui <insert the other flags>
```
When running ./configure check the output because mplayer needs alot of extra libs.
This will takes some tries to get it as you wish, when you are done.
```
make
sudo make install
```
Now it's installed you need to make some symblinks:
```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
```
if this doesn't work, try this one:
```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/share/mplayer/subfont.ttf
```

Now download the blue skin from mplayer site:
```
tar xjvf Blue-1.5.tar.bz2
mv Blue default
sudo cp -R default/ /usr/share/mplayer/Skin/
```

If you run gmplayer from the terminal and it complains about Something about sysctl.conf, do this:
```
sudo nano /etc/sysctl.conf
```
add:
**dev.rtc.max-user-freq=1024**
save and exit, and restart procps:
```
sudo /etc/init.d/procps.sh restart
```

---

### Post by Perfect Storm on 2006-09-02
You might want mplayerplug-in the latest as well (the one in the repo is quiet old):

Download the source from here: [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php)
Extract and cd into the folder
You also need mozilla-dev libs for this one. Then it's straight forward with ./configure make sudo make install.

---

