---
title: "help dvd player that works"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by jvicars on 2008-01-01
i cannot get a dvd player to work. i can video clips in the video file but it will not start a dvd and plan it. I am using Movie Player and Kaffine does not work either. I tried to dload vlc but  I could not get that either. i am sure this is simple. help.

---

### Post by bazzawill on 2008-01-01
Try mplayer I use it and it has never failed me for any format

---

### Post by CCNA_student on 2008-01-01
First, run the command
*sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot*

That will install Totem-xine, which is a good program to play DVD's. Then run

*sudo /usr/share/doc/libdvdread3/install-css.sh*

That will install libdvdcss2 which you need to get past the encryption that is on almost all DVD's.

---

### Post by wolfen69 on 2008-01-01
go to synaptic to see if you have libdvdread installed. then go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to get the dvd codecs.

---

### Post by Xavieran on 2008-01-01
I use gxine...
command:
sudo apt-get install gxine gxine-plugin xine libxine-extracodecs
To make DVD's auto-play when inserted go to System>Preferences>Removable Drives and Media ,go to the multimedia tab and change the command in Video DVD discs to gxine -a -f

---

### Post by jvicars on 2008-01-01
i went to the site you recommend. i am not sure what do download. i am sure its easy but i am totally new to linux. can you give me some easy instructions. thanks.

---

### Post by CCNA_student on 2008-01-01
Just copy and paste those commands I gave you into the terminal. That is what worked for me.

---

### Post by Xavieran on 2008-01-01
```
sudo apt-get install libdvdread3 libdvdnav4 libdvdplay0
```
should install the essentials...
then do:```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

and then:
```
sudo apt-get install gxine gxine-plugin xine libxine-extracodecs
```

---

### Post by crazyfish666 on 2008-01-04
> **bazzawill said:**
> Try mplayer I use it and it has never failed me for any format

I also now use mplayer, but I am having some problems. I could not get anything to play DVDs at first, when I installed totem-xine and tried to open Movie Player to use it Movie Player opened and immediately closed within half a second of opening. That was when I tried mplayer, which at least gave me an image, but the sound it was giving me was either some sort of a special feature interview of the extra commentary because it was certainly not the normal film. Then when I tried skip to the next chapter the whole screen of my computer went black gave me a full screen version of terminal (that is the best way I can think of to describe it). So I gave up on that and tried another DVD which seems to work a lot better, the sound lines up and it will skip to the next chapter, but when I press to skip to the next chapter it gives me an error which says "gnome_screensaver_control()", if I hit "ok" then the error message goes away and there seems to be no problem.

Anybody have any idea how to get the first DVD to work (it was Last Samurai if there is a possibility that ubuntu just doesn't like a particular DVD) and is there a real problem behind the error message? Anyone got any ideas about how to work Movie Player?

---

### Post by Techwiz on 2008-01-04
Download the program that is on this page [_[COLOR="RoyalBlue"]CLICK HERE[/COLOR]_!]("http://ubuntuforums.org/showthread.php?t=613462")
Then run it, choose the option install DVD codecs. Choose the correct system choice then let it do its thing. After it is done Movie Player (Totem) should be able to play DVDs.

---

### Post by CCNA_student on 2008-01-04
If you want to play a DVD first run this command in the terminal:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

and then run: 

sudo /usr/share/doc/libdvdread3/install-css.sh

This is where I got the commands from [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
This does work. Just try it.

---

### Post by crazyfish666 on 2008-01-04
> **CCNA_student said:**
> If you want to play a DVD first run this command in the terminal:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

and then run: 

sudo /usr/share/doc/libdvdread3/install-css.sh

This is where I got the commands from [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
This does work. Just try it.

Movie Player still closes immediately after opening. It only started doing this after I installed totem-xine. I am pretty sure that I had already run those two commands, I did do them a second time just now, however, to make sure that they didn't help and they don't. Mplayer seems to be my better bet, but it is still temperamental.

---

