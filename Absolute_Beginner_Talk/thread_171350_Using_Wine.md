---
title: "Using Wine"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by Suhgurim on 2006-05-06
Hi I'm new to Ubuntu and wine and i want to get morrowind installed and running does anyone know how to do this??

---

### Post by aysiu on 2006-05-06
Here's how to use Wine:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

I don't know if that applies to morrowind, though.

---

### Post by Sandlst on 2006-05-06
AFAIK Morrowind does not work on wine, only cedega, first go [here]("http://www.liflg.org/?catid=7"), download the loki installer, you can actually set the game up without installing cedega, so I would set up the game, then concentrate on cedega..  Also, cedega has a monthly fee, but if you compile it yourself it is free, the howto [here]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS") describes how to do this.  Post back if you have any problems, I would hate to try this stuff as a newbie.

---

### Post by Rinzwind on 2006-05-06
Morrowind seems to run under wine(x) but I see alot of problems :)

---

### Post by AndrewCaul on 2006-05-06
[QUOTE=aysiu]Here's how to use Wine:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

I don't know if that applies to morrowind, though.[/QUOTE]
I just read that.
Why *z:\home\username\.wine\drive_c\Program Files\Filezilla* rather than *C:\Program Files\Filezilla\*?

---

### Post by aysiu on 2006-05-06
[QUOTE=AndrewCaul]I just read that.
Why *z:\home\username\.wine\drive_c\Program Files\Filezilla* rather than *C:\Program Files\Filezilla\*?[/QUOTE] Wine sets up in the ~/.wine directory a little mini-fake-Windows environment, so it's best to try to go with that.

---

### Post by Suhgurim on 2006-05-09
ok i downloaded the loki installer but when i tyed to it i got

Verifying archive integrity... All good. Uncompressing Morrowind 1.2.0722-english Installer.......................................................................
/home/suhgurim/.setup8136: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


i also tryed to compile cedega but when i tryed to install 

cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev

i got

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


any ideas?

---

### Post by SkyNet2029 on 2006-05-10
Working backwards..  

> i also tryed to compile cedega but when i tryed to install 

cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev

i got

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

this needs to be issued as root (sudo) user, so I can only guesstimate that the sudo timed out during/after compiling of cedega. My thought would be to start out with this from Terminal:

$sudo -s      
    {to stay as root in Terminal and avoid the time-out (15 Min. i think) issues which lead to the 13 Permission Denied errors}

This also works wonders and saves frustrations with apt-build as well...

as for this part:
>  libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```
sudo apt-get install libgtk1.2
```   

should get things in order. Hope this helps!

---

### Post by Suhgurim on 2006-05-13
So far i've done everything the tutorialshave said and when i try to run morrowind i get this:

suhgurim@ubuntu:~$ cvscedega /usr/local/games/morrowind/Morrowind.exe
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:wave:ALSA_WaveInit open pcm: Device or resource busy
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:dialog:MSGBOX_OnInit system modal msgbox ! Not modal yet.
fixme:dialog:MSGBOX_OnInit system modal msgbox ! Not modal yet.

can anyone help?

---

