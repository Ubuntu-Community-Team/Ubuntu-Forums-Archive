---
title: "Internet Radio"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-10
How can I listen to ineternet radio?When I try to do that is shows me this dialog box:

An external application must bu launched to handle mms: links. Requested link: mms://espalhabrasas.sapo.pt/MegaFm

Application: totem “%”

In this box I click in Launch Application, but when totem starts it shows me this error:

Totem could not play 'mms://espalhabrasas.sapo.pt/MegaFM'.

No URI handler implemented for "mms".

---

### Post by Lopsicle on 2006-05-10
I got mine downloading automatix then checking the streamtuner box :)

---

### Post by kart3r on 2006-05-10
Can you explain yourself better?I'm new with linux :S

---

### Post by Lopsicle on 2006-05-10
No not really...Im new also

---

### Post by Obor on 2006-05-10
[QUOTE=Lopsicle]I got mine downloading automatix then checking the streamtuner box :)[/QUOTE]
If you don't have streamtuner yet download it through synaptic or type in terminal:
sudo apt-get update
sudo apt-get install streamtuner

(streamtuner will open your music player e.g xmms, once you click on the radio station)

if you need xmms:
sudo apt-get install xmms

or follow this guide: [here]("http://makuchaku.info/amnesty/#xmms")

---

### Post by cyracks on 2006-05-10
Don't know abaut totem I use amarok for which the procedure is folowing...
install amarok
install gstreamer engine
in amarok select gstreamer engine (settings->configure amarok->engine)
go to [http://www.shoutcast.com/](http://www.shoutcast.com/) and click with the right button on "tune in" and select "copy link address"
in amarok go tu playlist and add it do radio streams

---

### Post by kart3r on 2006-05-10
[QUOTE=Obor]If you don't have streamtuner yet download it through synaptic or type in terminal:
sudo apt-get update
sudo apt-get install streamtuner

(streamtuner will open your music player e.g xmms, once you click on the radio station)

if you need xmms:
sudo apt-get install xmms

or follow this guide: [here]("http://makuchaku.info/amnesty/#xmms")[/QUOTE]

I've installed streamtuner, but it keeps trying to open with totem and stills not working

---

### Post by kart3r on 2006-05-10
[QUOTE=cyracks]Don't know abaut totem I use amarok for which the procedure is folowing...
install amarok
install gstreamer engine
in amarok select gstreamer engine (settings->configure amarok->engine)
go to [http://www.shoutcast.com/](http://www.shoutcast.com/) and click with the right button on "tune in" and select "copy link address"
in amarok go tu playlist and add it do radio streams[/QUOTE]

I can't get gstreamer engine, it says: E: can't get gstreamer engine

---

### Post by Obor on 2006-05-10
[QUOTE=kart3r]I've installed streamtuner, but it keeps trying to open with totem and stills not working[/QUOTE]
If i remember right all I did was:
1. installed streamtuner
2. installed xmms
3. associated xmms with music files by typing the following, one by one in the terminal
> sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
sudo rm -f /tmp/defaults.*

and my radio works fine, you might need some codecs as well, if you don't have them yet. [Its all here]("http://easylinux.info/wiki/Ubuntu#Unofficial_Ubuntu_5.10_.28Breezy_Badger.29_Starter_Guide")

---

### Post by kart3r on 2006-05-10
I've done all as you said but it stills keep trying to open with totem =x

---

### Post by cyracks on 2006-05-10
[QUOTE=kart3r]E: can't get gstreamer engine[/QUOTE]

Do you have amarok-gstreamer installed ?

if you want to be able to play 'mms://espalhabrasas.sapo.pt/MegaFM' then you need gstreamer0.8-mms or gstreamer0.8-plugins installed.

If that don't work install amarok-xine and select xine engine it should also work.

---

### Post by kart3r on 2006-05-10
I've download all that and stills not working, i've tried xine engine and stills not works :X

---

### Post by AndyCooll on 2006-05-10
This might be because it is Firefox which is choosing which application to open a particular file with. 

I'm at work at the moment and having to use IE ( :( ), but if I remember correctly for Firefox it's something like Edit->Preferences->Downloads->Advanced and somewhere in there is the option to choose which application a file is associated with.

I think I had to tell Firefox to open pls files (which is what many radio stations use) with XMMS (or whatever player you wish to use)

Someone more knowledgeable might be able to confirm these details

:cool:

---

### Post by Kobalt on 2006-05-10
Try using mplayer instead of totem as a firefox plugin, it's not working quite well. To do so, check in your sources.list file ```
sudo gedit /etc/apt/sources.list
``` if this line is present : 


```
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse

```
If there is a " # " before the line, remove it, save & close the file. Then in command line type : 
```
sudo apt-get update
```

Then install mplayer and it's plugin : 
```
sudo apt-get install mplayer & mozilla-player
```

In order to read the stream you chose (mms = Windows media format), you need to install w32codecs. 
```
sudo apt-get install w32codecs
```

Enjoy!

---

### Post by Lopsicle on 2006-05-10
Yes I remember mine kept opening up in Totem at first, so I downloaded xmms then it was fine. Why not delete Totem and see if it will then open in xmms? you can always reinstall it afterwards?

---

### Post by glinsvad on 2006-05-10
nice to see a fellow sed-user :D

---

### Post by Virtuous on 2006-05-10
[QUOTE=Obor]If you don't have streamtuner yet download it through synaptic or type in terminal:
sudo apt-get update
sudo apt-get install streamtuner

(streamtuner will open your music player e.g xmms, once you click on the radio station)

if you need xmms:
sudo apt-get install xmms

or follow this guide: [here]("http://makuchaku.info/amnesty/#xmms")[/QUOTE]

I tried typing in terminal with:
sudo apt-get update Which went fine.

Then I tried typing in the terminal with:
sudo-apt-get install streamtuner and I got this in return:

@kubuntu:~$ sudo apt-get install streamtuner
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I don't know how to solve this. :(

---

### Post by Omnios on 2006-05-10
[QUOTE=Virtuous]I tried typing in terminal with:
sudo apt-get update Which went fine.

Then I tried typing in the terminal with:
sudo-apt-get install streamtuner and I got this in return:

@kubuntu:~$ sudo apt-get install streamtuner
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I don't know how to solve this. :([/QUOTE]

 Did you have synaptic open when you tryed apt-get it gives that error and you have to have it closed.

 ALso for my multimedia on the web I use Mplayer with the extra codecs and real player. I also installed the Media Player Connectivity extention for firefox. I can listen to shoutcast, Live 365 and other. A lot of it will count on your connection most of these players have crappy caching.

---

### Post by rocka on 2006-07-02
Hello all,

hope you don't me jumping into this thread...

I've just managed to get Ubuntu installed and updated, now I'm trying to get the basics working - like music, for a start...

If I understood the above correctly, I should install Automatix, then Streamtuner? And also, Synaptic is the thing you use to install programs in Ubuntu?
[pls correct me if I have the basics wrong... LOL]

...So I searched on "streamtuner" and also "automatix" in synaptic, but then what do you do? They show up on the left hand side of the window, but in the main part it says "no package is selected".

Double clicking or right clicking on them does nothing.

I went to the help file and it says to "select the package and choose the action from the package menu", but on that menu, all the options are greyed out and I cannot select them.

How do I get to the next step?

TIA,

---

### Post by Islington on 2006-07-02
[QUOTE=rocka]Hello all,

hope you don't me jumping into this thread...

I've just managed to get Ubuntu installed and updated, now I'm trying to get the basics working - like music, for a start...

If I understood the above correctly, I should install Automatix, then Streamtuner? And also, Synaptic is the thing you use to install programs in Ubuntu?
[pls correct me if I have the basics wrong... LOL]

...So I searched on "streamtuner" and also "automatix" in synaptic, but then what do you do? They show up on the left hand side of the window, but in the main part it says "no package is selected".

Double clicking or right clicking on them does nothing.

I went to the help file and it says to "select the package and choose the action from the package menu", but on that menu, all the options are greyed out and I cannot select them.

How do I get to the next step?

TIA,[/QUOTE]


I may be wrong, I am a noob as well.[Go here first.]("http://www.getautomatix.com/")These instructions worked for me:
> If you use Dapper, add this: 

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

If you use Breezy, add this:

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) breezy main

Kubuntu users, add this:

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) kubuntu main 

We haven't forgotten about you Mepis users:

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) mepis main 

The Automatix repository is GPG-secured, to make sure apt recognises our key, run these two commands in a terminal:

wget [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

Finally, enter "sudo apt-get update" in a terminal, and when its finished, "sudo apt-get install automatix
after that go to applications>>system>automatix
and then install streamtuner.
thats what I did, it seems to work.

---

### Post by rocka on 2006-07-02
Thank you very much for that tip - it worked, and as a bonus I learned something at the same time :)

In fact, let me say this about that package Automatix, and Ubuntu in general:

         WOW.

I just got a taste of the power of it - updated my Firefox with Java/Flash/etc and few other things like PDF reader etc, all at the same time. And at the end it said "no errors" !

Feels good (!)



The only little thing is, XMMS and Totem don't seem to want to play streams. They'll play local MP3 files ok, and as well as that I can play streams using VLC. I just need to right click on the playlist and select "open with..." But still, it would be interesting to know ***why***...

Thanks again...
;)

---

### Post by Islington on 2006-07-02
Glad it helped, Its pretty awesome, I keep wishing that my internet worked though, Cheers.

---

