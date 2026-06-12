---
title: "Lots of noob questions"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by pkroks on 2006-03-25
So I'm totally new to Ubuntu. Installed it last night when I was bored and I decided I wanted a change from windows. Sorry if the questions have already been asked before. 

Anyway, I have had a hard time. First things first, how do you install something? I tried to download a new theme for the desktop, and all it does is download a folder, what do I do? Where do I put the folder?

I tried to play music ( mp3 format) and I get an error message saying "This file is not an audio stream." What should I do? I tried playing it in the Linux equivalent of Windows Media Player, it said I should get codecs, where do I download codecs for linux?

I was told by a friend that I can activate and browse and use files in my windows partitions on my harddrives, how would I be able to do this? 

Please help a noob. ](*,)

---

### Post by carverj on 2006-03-25
regarding media codecs, a good place to start is Automatix.
simply do a search on this site (not necessarily limited to beginner community) for Automatix gui script. To install packages, you'll need to learn to use the command line, or alternatively you could begin by opening synaptic package manager in the menu for a list of packages which can be marked for installation. 
Good luck using Ubuntu

---

### Post by jamesford on 2006-03-25
yep grab automatix, also ahve a looka t the wiki, it should explain pretty much everything [http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

---

### Post by wolfee on 2006-03-25
try this then select files for wmv,avi or mpeg 

To install Automatix in Ubuntu do the following from terminal(one line at a time, pressing enter after each step):
Code:

wget [http://beerorkid.com/automatix/automatix_5.7-2_i386.deb](http://beerorkid.com/automatix/automatix_5.7-2_i386.deb) sudo dpkg -i automatix_5.7-2_i386.deb


To install Automatix in Kubuntu/Xubuntu do the following (one line at a time, pressing enter after each step):
Code:

sudo apt-get install xterm libglade2-0 libgnomecanvas2-0 wget [http://kambing.vlsm.org/ubuntu/pool/main/z/zenity/zenity_2.12.1-0ubuntu1_i386.deb](http://kambing.vlsm.org/ubuntu/pool/main/z/zenity/zenity_2.12.1-0ubuntu1_i386.deb) sudo dpkg -i zenity_2.12.1-0ubuntu1_i386.deb wget [http://www.beerorkid.com/automatix/automatix_5.7-2_i386.deb](http://www.beerorkid.com/automatix/automatix_5.7-2_i386.deb) sudo dpkg -i automatix_5.7-2_i386.deb


Automatix gets installed in Applications--> System Tools (GNOME)
and in main menu-->System (KDE/XFCE)

To run Automatix from terminal simply do:
Code:
try this when done select files you want for wmv
Automatix

To uninstall Automatix, do the following from terminal:
Code:

sudo apt-get remove automatix

Howto remember which options In Automatix u have already checked in the past : Open terminal and type
Code:

cat $HOME/automatix.log

---

### Post by wolfee on 2006-03-25
that didnt come out right just do what james said and go to link also after your done make sure to chech the box for frostwire which is just like limewire p2p!!!

---

### Post by zourcast on 2006-03-25
Perhaps you should also visit this site. I belive it will help you.

[http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/")

For the multimedia codecs, that site has all the help you need.

[http://www.ubuntuguide.org/#codecs]("http://www.ubuntuguide.org/#codecs")

Hope this helps you.

---

### Post by belikralj on 2006-03-25
Have you tried installing VLC player? I found it is the Windows Media Player equivelant in codecs that come with it and more, but not as fancy. It does the job, as well as playing all Video files WinMed can.

Just search for it in Synaptic Package Viewer.

---

### Post by pkroks on 2006-03-26
Well I tried that Automatix thing. I selected the packages I wanted and left it to download and install. Came back a while later and said everything was finished. Only problem was that when I went to open some of the applications I got error messages, from like more than half of them. I don't know why? 

So now I am going to try that site for downloading codecs. A friend also told me that I am probably using a wrong sound engine or something in the media player. But I can't find where to change the sound engine, I am just trying to play the mp3s in Rythmbox.

---

### Post by pkroks on 2006-03-26
I was also told to download BMPx player or something. I did, I installed it and it says I have missing dependancies or something. What should I do? 

I am also about to try to search for VLC player in the synaptic package manager.

---

### Post by mneptok on 2006-03-26
To play mp3s with Rhythmbox install the gstreamer-mad package via Synaptic. Simple.

---

### Post by pkroks on 2006-03-26
OK. So I went to the synaptic package manager and tried to install gstreamer-mad or whatever. It came up with 

gstreamer0.8-mad:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable


What should I do? Install libid3tag and libmad or something?

---

### Post by mneptok on 2006-03-26
Be sure to enable the Universe and Multiverse repositories in Synaptic. Then try again.

---

### Post by zourcast on 2006-03-26
[QUOTE=mneptok]Be sure to enable the Universe and Multiverse repositories in Synaptic. Then try again.[/QUOTE]

If you don't know how to do this, go here

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse")

As you are guiving your first steps in linux, I would also advice you to take a look a this guide

[http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User's_Guide]("http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User's_Guide")

---

### Post by pkroks on 2006-03-26
Cool. I managed to get the sound working. Now I want to install nVidia drivers. I downloaded the IA32 installer file from nvidia.com. I tried just installing it. It told me I had to be in the root user account. So I tried sudo su root. Entered the password. Started the install again, this time it gave me an error. This is what it says:

Error: Unable to find the system utility 'ld' ; please make sure you have the package 'binutils' installed. If you do have binutils installed, then please check that 'ld' is in your PATH. 


What does that mean?

---

### Post by pkroks on 2006-03-31
Ok. Well I got the nVidia driver working. 

Now I have just tried to get Opera working, the internet browser. I went into the terminal and typed "** sudo apt-get install opera **" It downloaded and installed the browser. However I get the following message when I open Opera. What should I do?

```
Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/netscape/plugins-libc6/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
/usr/lib/netscape/plugins-libc6
```

---

### Post by pkroks on 2006-03-31
... bump

---

### Post by erniewinner on 2006-03-31
:-?  you could download firefox! :mrgreen:

---

### Post by Mustard on 2006-03-31
For Opera read this page..

[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

