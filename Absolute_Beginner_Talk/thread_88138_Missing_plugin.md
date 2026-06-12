---
title: "Missing plugin"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Freakiej on 2005-11-09
Hello,

Excuse me for my bad english, I speak dutch and I'm just 15 :)

I installed today Ubuntu. I've never worked before with this OS. 
I'm sure you can help me with my problem.

I wanna play .mp3-files, but I get this error:
Please instal the plugin

I was searching on google and I found this link:
[http://www.free-codecs.com/download/MPEG_Layer_3_Codec.htm](http://www.free-codecs.com/download/MPEG_Layer_3_Codec.htm)
I tried to instal it but this error appears:

Kan lokatie niet weergeven
file:///usr/share/ubuntu-artwork/home/index.html
Kan ''/home/admin/Desktop/l3codecx.exe'' niet weergeven

I think this is the english error:
Cann't reproduce the location
file:///usr/share/ubuntu-artwork/home/index.html
Cann't ''/home/admin/Desktop/l3codecx.exe'' reproduce

Can someone help me?

Simon

---

### Post by earobinson on 2005-11-09
this should help you out a lot [http://ubuntuguide.org/](http://ubuntuguide.org/) (its for version 5.04 but what you need will work for 5.10)

*extra points for searching before you post* and your english is great!

---

### Post by Freakiej on 2005-11-09
Thanks for the link!
It seems very intresting!

---

### Post by Freakiej on 2005-11-10
I don't understand it :(
Could you help me?

I'm trying to install the Multimedia Codecs.

At first I launch Root Terminal
Secondly I give this commands:
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

It goes by the first command wrong. I got this error:

root@freakiej:/home/admin # sudo apt-get install gstreamer0.8-plugins
Pakketlijsten worden ingelezen... Klaar (Ready/done)
Boom van vereisten wordt opgebouwd... Klaar (Ready/done)
Pakket gstreamer0.8-plugins is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket gstreamer0.8-plugins heeft geen installeerbare kandidaat

Packet Gstreamer0.8 plugins are not available, although another program reffered to it.
It could mean that this packet is missing, aged or is only available of another source.
E: Packet gstreamer0.8-plugins has no instalable candidate.

Could you help me?
I'd be very happy when I could listen music on Ubuntu.

Regards,
Simon

---

### Post by BoyOfDestiny on 2005-11-10
[QUOTE=Freakiej]I don't understand it :(
Could you help me?

I'm trying to install the Multimedia Codecs.

At first I launch Root Terminal
Secondly I give this commands:
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

It goes by the first command wrong. I got this error:

root@freakiej:/home/admin # sudo apt-get install gstreamer0.8-plugins
Pakketlijsten worden ingelezen... Klaar (Ready/done)
Boom van vereisten wordt opgebouwd... Klaar (Ready/done)
Pakket gstreamer0.8-plugins is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket gstreamer0.8-plugins heeft geen installeerbare kandidaat

Packet Gstreamer0.8 plugins are not available, although another program reffered to it.
It could mean that this packet is missing, aged or is only available of another source.
E: Packet gstreamer0.8-plugins has no instalable candidate.

Could you help me?
I'd be very happy when I could listen music on Ubuntu.

Regards,
Simon[/QUOTE]

sudo apt-get install beep-media-player

I know this is sort of a workaround, until you get all the other stuff installed. You will be able to play mp3's and listen to streaming web radio etc (beep is similar to winamp)

---

### Post by earobinson on 2005-11-10
When your in the root terminal you do not need to use sudo just type the command.

Try loading synaptic and installing them like that, you may have broken packeges and synaptic will fix them.

---

### Post by Freakiej on 2005-11-10
[QUOTE=BoyOfDestiny]sudo apt-get install beep-media-player
[/QUOTE]

This doesn't workl
Terminal gives this error:
E: Cann't find the packet beep-media-player

(I translated it, the error is maybe different in english)

By the way: 
1. What is the difference between terminal and root terminal?
2. What does the command sudo apt-get exactly mean? 
3. Where can I find a list with commands? I mean, in Windows XP, I use commands like: ipconfig, netstat, dir, xcopy etc. Got Ubuntu this also?

@earobinson -> how does synaptic work? I don't see a option to load packeges or a option to install downloaded packeges.

---

### Post by earobinson on 2005-11-10
can you post your repo's (cat /etc/apt/sources.list)

1. terminal is just the normal user you can not do anything that needs root rights (think of root as admin)

2. there are 2 commands there sudo ([http://www.hmug.org/man/8/sudo.php](http://www.hmug.org/man/8/sudo.php)) and apt-get ([http://www.die.net/doc/linux/man/man8/apt-get.8.html](http://www.die.net/doc/linux/man/man8/apt-get.8.html)) you can also type man sudo, or man apt-get (or man <any other comand>) for info

3. apropos is a good command to search for a command or you can look at [http://www.ubuntuforums.org/showthread.php?t=83408&highlight=commands](http://www.ubuntuforums.org/showthread.php?t=83408&highlight=commands) (i found this by searching the forums for: commands)

---

### Post by earobinson on 2005-11-10
> [14:48] simondejong1: hey\
[14:48] simondejong1: I hope you don't mind that I added you
[14:49] earobinson222: i got no clue who this is
[14:50] simondejong1: [http://ubuntuforums.org/showthread.php?p=480606#post480606](http://ubuntuforums.org/showthread.php?p=480606#post480606) i'm freakiej
[14:50] earobinson222: ic, nope i dont mind at all, wouldent post it if i minded
[14:50] simondejong1: i don't understand your last post: can you post your repo's (cat /etc/apt/sources.list)
[14:51] earobinson222: lol im not on my computer right now at work
[14:51] earobinson222: in the terminal type cat /etc/apt/sources.list
[14:51] simondejong1: ok her it's almost 9 PM (holland)
[14:51] earobinson222: lol im not on my computer right now at work (so i may have got the exact command worng)
[14:51] simondejong1: ok, tnx
[14:51] earobinson222: that should list your repo
[14:52] earobinson222: and it should look like this
[14:52] earobinson222: it should look like this [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
[14:53] simondejong1: I got this: deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main r estricted and very much other sh*t
[14:53] earobinson222: u are using 5.10 right?
[14:54] earobinson222: its listed at the bottom of the site
[14:54] simondejong1: thank you!
[14:54] simondejong1: i'm gonna try it!
[14:54] earobinson222: if your using 5.04 thats listed 2
[14:54] simondejong1: but i got to go
[14:54] earobinson222: if yours looks like that you should be able to run the commands
[14:54] earobinson222: no problem
[14:54] simondejong1: thanks for ur advice!
[14:54] earobinson222: mind if i post this convo to the site?
[14:55] simondejong1: not at all!
[14:55] earobinson222: help other people if they have the same problem
[14:55] earobinson222: kk good luck
(Just a note yes my IM is posted but im not always there, you can always try me at my IM but you may or may not get a responce, but I do not mind at all being contacted :))

---

### Post by Freakiej on 2005-11-10
I see this:

root@freakiej:/home/admin # cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

I think it looks a little bit like this one: Hoary (5.04)

---

### Post by earobinson on 2005-11-10
Ok, you need to make yours look like the hoary 5.04 one.

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse 

you can do this by typing sudo gedit /etc/apt/sources.list in the terminal (not root terminal)

then do an apg-get upgrade or update (not sure which one and im not on my computer do both to be safe) you could also run synaptic and click refresh.

---

### Post by Freakiej on 2005-11-12
It works.
Thanks guys!!! I'm very grateful!

---

