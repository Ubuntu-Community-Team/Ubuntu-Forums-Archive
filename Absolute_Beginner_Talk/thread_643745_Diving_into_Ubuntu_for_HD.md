---
title: "Diving into Ubuntu for HD"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by iSplicer on 2007-12-18
Hi all

I am eager to use ubuntu for my HTPC that is hooked into my 1080p projector. But before I dive in, I would like to ask a few questions:

1. I want to run it at A resolution of 1920x1080. How Easy is this to setup? (I have an ATI X1600XT - I heard from somewhere that ubuntu was a pain to set up with ATI... Is this true?)

2. I will mainly run x264 .mkv video files. The obvious choice is VLC Player. Does this come with all required codecs and filters? If not, are they available, like the CCCP pack for windows?

3. How fast does it usually start up? I have a E6000 and 2GB of RAM.

Thanks in advance!

---

### Post by nowshining on 2007-12-18
1. I want to run it at A resolution of 1920x1080. How Easy is this to setup? (I have an ATI X1600XT - I heard from somewhere that ubuntu was a pain to set up with ATI... Is this true?)

A) can't really answer i also heard but i never used an ATI card.


2. I will mainly run x264 .mkv video files. The obvious choice is VLC Player. Does this come with all required codecs and filters? If not, are they available, like the CCCP pack for windows?

Yes, maybe and prob. NO, i haven't used VLCplayer u gotta download it and try it out, and if u didn't know u can download and install apps from the live cd itself and test em' out but after a reboot they will be gone, system --- administration -- synaptic package manger for VLC player i think. IF u don't get all the codecs u'll need to find in synaptic the needed libraries and install them.


3. How fast does it usually start up? I have a E6000 and 2GB of RAM.

faster than windows at least and i'm guessing faster on urs than mine if u have a newer machine then yes itta be faster.

---

### Post by hyper_ch on 2007-12-18
x264 codecs are available... I used them to create some .mkv myself (that was the thread that made me use x264: [http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)) and you'll see there that you'll need to isntall the codecs:

```

sudo apt-get install x264-bin

```

Not sure if you need to install more, you'll see when you try it.

--> starting up
Depends on what you want to load upon booting ;9

---

### Post by iSplicer on 2007-12-18
Thanks for ur replies... could someone please give me more advice on question 1? Thanks

---

### Post by Thelasko on 2007-12-18
Just a suggestion. Try [Mythbuntu]("http://en.wikipedia.org/wiki/Mythbuntu").

---

### Post by nowshining on 2007-12-18
> **iSplicer said:**
> Thanks for ur replies... could someone please give me more advice on question 1? Thanks
well, u'll have to do ur own external research via a search engine on that one or search the forums and read ati posts and so forth.

---

### Post by iSplicer on 2007-12-18
> **Thelasko said:**
> Just a suggestion. Try [Mythbuntu]("http://en.wikipedia.org/wiki/Mythbuntu").

Will that work with a DTV 1000T card?

Any more advice on running ubuntu with ati card on 1920x1080 resolution?


Thanks

---

### Post by nowshining on 2007-12-18
using mythbuntu or any devain/ubuntu and basically any linux distro will take some manual setting up to do on some things and or to get some hardware to work. These involve either one or more of the following (ur mileage may vary):

1.)editing .conf files
2.)using the terminal for commands u may have to do
2.)command line interface (esp. if something happens where u can't get a gui running, but u'll still have access to he basic system and the ability to read files and edit them which is easy one u learn how to do it) also u'll prob. have to go thru the cli to edit ur xorg.conf file with a cli editor and edit there, i suggest nano easy to use and learn. :)

---

### Post by PhoenixP3K on 2007-12-18
Concerning the graphics card I found that installing ATI drivers wasn't too hard, I would dare say just as simple as installing drivers on Windows. However I have not tested x1600 myself under Linux and don't know of any specific issues concerning it. I'm pretty sure you should be fine and will find a lot of posts about this in the forums.

---

### Post by ByteJuggler on 2007-12-18
> **iSplicer said:**
> Hi all
1. I want to run it at A resolution of 1920x1080. How Easy is this to setup? (I have an ATI X1600XT - I heard from somewhere that ubuntu was a pain to set up with ATI... Is this true?)


Some ATI's chipsets are worse than others.  That said, I have only ATI cards at the minute (R200 based integrated mobile whatsit on an HP Laptop, some form of X1300/X1550 series in a "server" Dell box, a 9800XT in my main desktop rig (old) and a new X3850 Pro that's due to go into my desktop rig as cheap upgrade.  I've been able to make all of them work relatively well (including desktop effects to a lesser or greater degree depending on which card you look at.)  The X3850 is the poorest at the minute, due to the simple fact that it's too new and isn't properly supported yet anywhere.  I expect you should be able to get it to work fine. (My desktop res btw is also widescreen 1680x1050 so I suppose your setup is not too far off from that.)

Hope that helps.

---

