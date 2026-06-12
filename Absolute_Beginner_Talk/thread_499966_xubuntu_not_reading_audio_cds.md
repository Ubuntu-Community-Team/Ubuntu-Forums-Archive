---
title: "xubuntu not reading audio cds"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Haus Neuerburg on 2007-07-13
Hi there,
my cd-drive does not read any audio cd anymore. Neither ordinary music cds nor mp3-files. It just does not show up on the desktop or in the filemanager so that I cannot mount it.
I'm able to play *.mp3 files which are stored either on the HDD or on an usbstick. Does any one have any idea what I could do about it? The cd-drive itself seems to be ok as it can read data and picture cds.
Thanks a lot for any hint
Haus
P.S. I'm running xubuntu 6.06.1 as sole OS

---

### Post by twiceasworn on 2007-07-13
I would suggest checking your logs files.  Most likely there is something interesting in there pertaining to the error.

I would check /var/log/messages and /var/log/syslog   If you have a hard time reading through it, post it and I will have a look at it.

---

### Post by Haus Neuerburg on 2007-07-13
ok, will check that as soon as I've the children off their icq conversation...;-)....'ta

---

### Post by twiceasworn on 2007-07-13
Right on :)

---

### Post by tjotser on 2007-07-13
Ahh , my first problem with Xubuntu when i started using it... You have to mount your CD's manually.
I am a big fan of xubuntu but i am not on the distrro right now, just regular feisty. IF I REMEMBER CORRECTLY :
Right-click on your top desktop bar, and select "add to panel"/or/"add item" -i forgot what it's called-
then select the diskmounter to be added, (yellow-green-blue-icon), Next click on the added panel iterm, and you will see all devices, but your CD drive is in RED "not mounted" or something... click on the device and it will mount..

Hope i am right about this, good luck !:KS

---

### Post by Haus Neuerburg on 2007-07-13
@tjotser: I've actually got that feature on my panel: the problem is that the computer does not accept any ordinary audio cd: as it is not shown on the desktop either I cannot mount it with right-click=>mount volume or see it anywhere in the file directory. If I click on my cd drive in the discmounter nothing happens (logically, as the machine doesn't recognize anything in there.

@twiceasworn: indeed I do have a hard time reading through it as I haven't got a clue which info you need, I have to admit. For a first try I'll post the bits and pieces obviously relating to the cd drive:
from /var/log/messages:
Jul 13 22:35:15 ubuntu kernel: [   32.561658] hdb: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
Jul 13 22:35:15 ubuntu kernel: [   32.561690] Uniform CD-ROM driver Revision: 3.20
...
Jul 13 22:35:15 ubuntu kernel: [   67.367731] cdrom: open failed.
...
Jul 13 22:35:39 ubuntu kernel: [   97.644984] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Jul 13 22:35:39 ubuntu kernel: [   97.645015] hdb: drive_cmd: error=0x04 { AbortedCommand }
...
Jul 13 22:49:48 ubuntu kernel: [  945.498155] cdrom: open failed.
Jul 13 22:49:49 ubuntu kernel: [  945.881344] cdrom: open failed.
Jul 13 22:50:53 ubuntu kernel: [ 1010.706580] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jul 13 22:50:53 ubuntu kernel: [ 1010.706612] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jul 13 22:50:53 ubuntu kernel: [ 1010.706630] ide: failed opcode was: unknown
Jul 13 22:50:53 ubuntu kernel: [ 1010.706647] end_request: I/O error, dev hdb, sector 64
Jul 13 22:50:53 ubuntu kernel: [ 1010.709492] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16
Jul 13 22:53:29 ubuntu kernel: [ 1166.717658] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jul 13 22:53:29 ubuntu kernel: [ 1166.717692] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jul 13 22:53:29 ubuntu kernel: [ 1166.717756] ide: failed opcode was: unknown
Jul 13 22:53:29 ubuntu kernel: [ 1166.717777] end_request: I/O error, dev hdb, sector 64
Jul 13 22:53:29 ubuntu kernel: [ 1166.870211] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16

from /var/log/syslog:
Jul 13 22:35:15 ubuntu kernel: [   31.825972] hdb: CD-532E-B, ATAPI CD/DVD-ROM drive
Jul 13 22:35:15 ubuntu kernel: [   31.889745] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 13 22:35:15 ubuntu kernel: [   31.890735] Probing IDE interface ide1...
...
Jul 13 22:35:15 ubuntu kernel: [   32.561658] hdb: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
Jul 13 22:35:15 ubuntu kernel: [   32.561690] Uniform CD-ROM driver Revision: 3.20
..
Jul 13 22:49:48 ubuntu kernel: [  945.498155] cdrom: open failed.
Jul 13 22:49:49 ubuntu kernel: [  945.881344] cdrom: open failed.
Jul 13 22:50:53 ubuntu kernel: [ 1010.706580] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jul 13 22:50:53 ubuntu kernel: [ 1010.706612] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jul 13 22:50:53 ubuntu kernel: [ 1010.706630] ide: failed opcode was: unknown
Jul 13 22:50:53 ubuntu kernel: [ 1010.706647] end_request: I/O error, dev hdb, sector 64
Jul 13 22:50:53 ubuntu kernel: [ 1010.709492] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16
Jul 13 22:53:29 ubuntu kernel: [ 1166.717658] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jul 13 22:53:29 ubuntu kernel: [ 1166.717692] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jul 13 22:53:29 ubuntu kernel: [ 1166.717756] ide: failed opcode was: unknown
Jul 13 22:53:29 ubuntu kernel: [ 1166.717777] end_request: I/O error, dev hdb, sector 64
Jul 13 22:53:29 ubuntu kernel: [ 1166.870211] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16
 
The error messages relate to my attempt of playing an ordinary audio cd. Does xubuntu need some more codecs to be able to read/play the cd? On the other hand I do not think that this is the problem as I can listen to mp3-files from other sources (I actually copied them from the cd to a sd-card-on a different computer though)
Help is needed:confused:

---

### Post by crimesaucer on 2007-07-13
You can install Grip on xubuntu to have playback for CD's.


Grip will also rip your CD's and encode them.


Grip: [http://nostatic.org/grip/](http://nostatic.org/grip/)


...you could even have a my SQL-based MP3 jukebox if you install Digital DJ with it: [http://nostatic.org/ddj/](http://nostatic.org/ddj/)

---

### Post by Haus Neuerburg on 2007-07-14
@ crimesaucer: what exactly is grip and what does it do?
I could audio cds and they were recognizied by the system before I had installed evolution 2.6. Which files/codecs might it have disabled?

---

### Post by crimesaucer on 2007-07-14
Grip is a program that will play your CDs like a music player...plus


...it's a few different things, you should check out the link and read up on it a bit. 


I had problems playing CD's on xubuntu when I first installed xubuntu last Sept/Oct. 


Plus, I couldn't rip my CD's properly with any other CD ripper (Sound Juicer, Goobox, and a few others). Grip will rip your CD's perfectly, and encode them into mp3, ogg, or flac, at any bitrate you choose.


Check out Ubuntu Forums Search feature and "Grip" to learn the best way to encode.


Grip can even be a my SQL-based MP3 jukebox (with Digital DJ)...I haven't tried that yet, but it might be a pretty cool way to store your music collection, especially if it is a large collection.

---

### Post by crimesaucer on 2007-07-14
Basically, when I put an audio CD into my computer, nothing happens.


But if I then open up my Grip, it is cued up and ready to play, all I have to do is press play: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-44-7.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-44-7.png)


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-44-6.png[/IMG]

---

### Post by Haus Neuerburg on 2007-07-14
@ crimesaucer: thanks, I can now listen to audio cds. But why did it work with xfmedia before the evolution install and stopped working afterwards?
with grip the cd is still not shown on the desktop/in the file directory-but I have more music
Thanks a lot Haus

---

### Post by crimesaucer on 2007-07-14
I never had the ability to playback a CD since 6.06 (I'm on 7.04 now)...I can play a CD with data on it, or movies, or a DVD with data and movies, and even a DVD with chapters...but I was unable to play music since my first install.


Grip was one of my first programs that I installed because I had this problem...and it's worked perfectly ever since...it's even easier to use because it has the eject button and all of the other buttons and things...plus you can minimize it.


Then latter when I was trying to rip CD's, Grip turned out to be a lot better then anything else because of all the advanced settings that you could do.


As soon as I get a new device, I'm going to rip my collection again and encode it into flac because I don't like how mp3/ogg/wma sounds compared to a CD.

---

### Post by 320blues on 2007-07-15
thanks for posting this.  i'm running xubuntu 7.04 and have loaded one player after another.  one will seem to work like i want, then seems to go sideways or something.  i'll try grip. 
i'm still a bit confused about something though-should i or should i NOT run regular ubuntu packages as a rule?  primarily multimedia.  my machine is a dell gx150/1g/384mb.  i have an ati rage 128 (oh well) at present.

---

### Post by crimesaucer on 2007-07-15
I install all of these codecs: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

..and I like the combo of the Exaile! media player for .ogg .mp3 and my library...and Grip for audio CD's and ripping/encoding.

install Exaile!: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Music_Manager_and_Player_.28Exaile.21.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Music_Manager_and_Player_.28Exaile.21.29)


Exaile! homepage: [http://www.exaile.org/](http://www.exaile.org/)

---

