---
title: "DVD not working"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-03-24
Strangely  my DVD drive won't play music although I've used it to install Xubuntu onto my laptop.  If I go to system >discs > and click on the dvd drive it shows the number of song titles on the CD in the drive and it gives me the option to play the disc, but when I select play nothing happens. Other operating bleeps and sounds come from the laptop so I'm assuming the sound card is working.  Can someone help please?

---

### Post by Bachstelze on 2007-03-24
Have you tried to run a media player and select "Play audio CD" from within it ?

---

### Post by a.v.l on 2007-03-24
> **HymnToLife said:**
> Have you tried to run a media player and select "Play audio CD" from within it ?

I only have xfmedia and it doesn't show the content of the CD.

---

### Post by euler_fan on 2007-03-24
My lappy has one of those combo drives and I use VLC successfully to play music and dvd's. It's in the repos and add/remove programs. If you want dvd's go to the ubuntu install page on their website and it has the package to download to make them work.

---

### Post by a.v.l on 2007-03-24
> **euler_fan said:**
> My lappy has one of those combo drives and I use VLC successfully to play music and dvd's. It's in the repos and add/remove programs. If you want dvd's go to the ubuntu install page on their website and it has the package to download to make them work.

Thanks for the advice, unfortunatly this hasn't helped.  I've just installed automatix and  all the codecs from there and also installed real player 10 also m/player and vlc.  

At the moment I have some improvement in that I can play a DVD, but the picture is jerky almost like loading one frame at a time, in XP this worked fine. The sound on the DVD is ok for a short while then disapears completely.  

I am still unable to play a music CD or see the content of the CD at all, no matter where I look for it.  Perhaps another CD player may work, any suggestions please?  I seem to remember seeing something about a missing  codec that may cause a jerky DVD/film movement,  but unfortunatly I have forgotten where I saw this information.  I am quiet close I am getting close to a working laptop having relaced the XP OS.  This has taken me many weeks of trying different varieties of Linux. Now if only  I could fix the DVD/CD player!!!

---

### Post by euler_fan on 2007-03-24
Odd. And you installed VLC using Add/remove? It may be worth it to uninstall and use the instructions from [here]("http://www.videolan.org/vlc/download-ubuntu.html"). Doesn't take that long and the instructions are pretty good IMHO. Looking at the page I linked, they say the version in the standard repos is very old. That might be part of the issue.

Good luck!

---

### Post by a.v.l on 2007-03-25
I am making good progress, the CD music disc recognition problem I had is now resolved by installing "Rhythmbox" from the repositories.  I have also installed a few codecs from the official Ubuntu book which has improved the DVD sound quality.  

I am still looking for an answer to my DVD movies viewing problem, which still has a jerky action to the movie. I'm so close now I just need that final fix for DVD movie showing, so would appreciate and further advice.  Is there another program I can use to show movies besides Totem?

---

### Post by euler_fan on 2007-03-25
Please see my previous post. I pretty much swear by the current version of VLC.

---

### Post by a.v.l on 2007-03-25
> **euler_fan said:**
> Please see my previous post. I pretty much swear by the current version of VLC.

I need some help in following theinstructions in the  link you sent. call it inexperience.  Would you be able to talk me through each stage please.

---

### Post by euler_fan on 2007-03-25
Sure.

Into the Command Line!

Start the terminal and type
```
sudo nano /etc/apt/sources.list
```
Enter your password when prompted. Expect to every time you type "sudo <anything>". You won't see your password (or anything at all) as you enter it, but don't worry, it will tell you if you get it wrong :)

Go to the bottom of what you see (scroll down using the arrow keys) and copy the following two lines:
```
# Repo for Updataed VLC Player
deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe
```
They type Control+o to save (nano uses the ^ symbol for ctrl) followed by ctrl+x. This will save your work and exit.

Now enter the following two commands one at a time:
```

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2

```
The first updates your sources list, the second installs vlc and some handly plug-ins. The last one is the DVD codec you need.

That should be it.

---

### Post by a.v.l on 2007-03-25
> **euler_fan said:**
> Sure.

Into the Command Line!

Start the terminal and type
```
sudo nano /etc/apt/sources.list
```
Enter your password when prompted. Expect to every time you type "sudo <anything>". You won't see your password (or anything at all) as you enter it, but don't worry, it will tell you if you get it wrong :)

Go to the bottom of what you see (scroll down using the arrow keys) and copy the following two lines:
```
# Repo for Updataed VLC Player
deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe
```
They type Control+o to save (nano uses the ^ symbol for ctrl) followed by ctrl+x. This will save your work and exit.

Now enter the following two commands one at a time:
```

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2

```
The first updates your sources list, the second installs vlc and some handly plug-ins. The last one is the DVD codec you need.

That should be it.


I did everything above and inserted a DVD totem opened and said libdvdcss2 wasn't installed. Looked for it in the repositories and got this message. 

libdvdcss2:

Package libdvdcss2 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by euler_fan on 2007-03-25
Try opening the DVD with VLC. it should be under Applications -> Sound and Video.

Then with the DVD in, go to file -> open disk, tell it what kind of disc it is (DVD with or without menus) and see what happens. I don't use totem, and have yet to get a disk working with it, but they work fine in VLC.

If that doesn't work, please go into synaptic and search for libdvdcss2 and check if it is installed and post what you find.

---

### Post by a.v.l on 2007-03-26
libdvdcss2  appears in the repositories and yet I'm unable to correct the problem.  Totem tries to play a dvd but then ejects the disc saying I am trying to play it without libdvdcss2.  I tried another dvd player which played a little jurkily and I then had a message which said:

" The amount of dropped frames is too hight, your system might be slow, not properly optimised or just to loaded"

My system is a Pentium 4 processor 256mg of RAM and a 40 gig HD  This laptop seems to be particular in what it lets run, and yet XP worked fine including showing DVD's. Today I've tried puppy linux and had better success in viewing a DVD but have now decided to try a re-install of Xubuntu.  My previous installation of Xubuntu was using  "safe graphics mode" as I failed to install the OS without doing this.  Could this have anything to do with my DVD viewing troubles? Anyway I'm presently reinstalling in the non safe graphics mode and will keep you informed of my progress.  Thanks for your help.

---

### Post by a.v.l on 2007-03-26
Installing Xubuntu without it being in the safe graphics mode failed I'm afraid and caused my laptop to show no images on the monitor just a blank screen. When installed in safe graphic mode, I could play and see a DVD film but it had a very jerky unacceptable action. 

Having tried to resolve this with the forums help as well as trying other linux systems over the last three days I have to admit I failed to find one which works well enough on this laptop, a Samsung V25.  In desparation I've had to re-install XP and to my slight annoyance it worked right away DVD films worked first time as did everything else. I still have Linux on my other three PC's which all work and will be staying put, but unless someone can advise me of another Linux OS that may work on this laptop, I'm going to have to stay with XP for a while longer. Thanks again guys your help has been much appreciated  :( 

OS's I've tried on this laptop. 

Ubuntu
Xubuntu
Puppy Linus
DSL
Zenwalk Core
Koppix
Sabayon Linux mini

---

### Post by rstevesat on 2007-04-03
hi Euler ,
                 I tried your suggested commands but seems that some dependencies and are not there .this was the message i got :



rj@rj-laptop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
                      Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
  vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
       Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5) but it is not installable
       Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.5) but it is not installable
       Depends: libxosd2 (>= 2.2.13) but it is not installable
  vlc-plugin-esd: Depends: vlc-nox but it is not going to be installed
                  Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
E: Broken packages






Any other way!

---

### Post by euler_fan on 2007-04-04
Are the universe repositories enabled?

Otherwise, not sure what to say.

---

### Post by XerXeX on 2007-11-29
I get the exact same message: "Package libdvdcss2 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list"

How do I move on?

---

