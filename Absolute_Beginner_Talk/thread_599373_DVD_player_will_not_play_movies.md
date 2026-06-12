---
title: "DVD player will not play movies"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Covalent Bond on 2007-11-01
Have looked at other posts and still can not get get my DVD player to play commercial movies. Have tried both Totem and Gxine; Totem says there are "no plug ins to handle this movie"; Gxine message reports "no demuxer found-stream format not recognized." For Gxine I followed instructions provided at a Ubuntu site and installed the following: gxine, llibdvdnav4, installed libdvdread3-css.sh, and in Removable Drive, multi-media tab typed "gxine -S dvd:/". I can't recount all I have done with Totem trying numerous approaches as suggested in various posts.  

I am becoming increasingly frustrated with Linux because I do not understand how one would know about some of the seemingly Byzantine commands needed to get something to work.  As is obvious, I am very green with Linux, and any help needs to be practically idiot proof.

Thanks for any and all help offered.
CB
_

---

### Post by philinux on 2007-11-01
This thread used to be a sticky in this forum but appears to have moved to multimedia. However this is what I did and got it sorted.

[http://ubuntuforums.org/showthread.php?t=413625](http://ubuntuforums.org/showthread.php?t=413625)

dont blame linux it's to do with legal stuff etc.

---

### Post by LowSky on 2007-11-01
try VLC, it plays everthing

---

### Post by Pumalite on 2007-11-01
sudo apt get install ubuntu-restricted-extras
Install Medibuntu repo:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by Covalent Bond on 2007-11-01
I edited the APT Source List as recommended by Philinux, I also installed the Medibuntu Repository as recommended by Pumilite, and nothing changed.  Still unable to play a DVD movie.  Should I remove both Gxine and Totem and start from scratch, installing VLC?  Maybe I will go back to reading books, they appear about as technologically advanced as I can handle at this time.

Thanks for your forbearance

CB.

---

### Post by philinux on 2007-11-01
gxine and totem and vlc are all just different media players.

What happens when you put dvd in. Does an icon appear on your desktop?

does a player try to start , any error messages. 

On mine the icon appears and totem starts but I've found this isn't very good I nearly always start mplayer or vlc to play a dvd.

---

### Post by Covalent Bond on 2007-11-01
Philinux:

When I put in a DVD movie, I do get an icon on the screen, but first Gxine starts up, and I get this message:  "X engine failed to start  No Demuxer".  I close out and attempt to start Gxine via the Applications menu and get the same message.  I tried the same thing with Totem, and I get a message "no plug in to handle this movie".  Previously, I went to the Ubuntu site, Playing DVDs, and installed Gxine, Libdvdnav4, DVDcss2, and Libdvdread3; however, I did not find Libdvdplay0 in Synaptic Manger.  Don't know if this is significant.  Googled that file, but was uncertain how to download and install the file, assuming it is needed.

Thanks,
CB

---

### Post by Pumalite on 2007-11-01
Can you pay songs in your computer?

---

### Post by Covalent Bond on 2007-11-01
Pumalite:

Can play songs; in fact, am listening to a CD now.

CB

---

### Post by Pumalite on 2007-11-01
Install VLC. It comes with all the codecs in one package.

---

### Post by meg23 on 2007-11-01
Yeah, VLC will really play everything.

---

### Post by Covalent Bond on 2007-11-01
Pumalite:

Took your advice and installed VLC, it seems to work.  I will still try and noodle around with Totem and/or Gxine to get one of them to work, but at least I will be able to view movies on my PC now.

Thank you everyone for your advice and support.
CB

---

### Post by click4851 on 2007-11-15
following your steps with gxine...... try this package

libxine1-ffmpeg

Worked for me, better dvd nav, good luck.

---

### Post by Raggnarok on 2008-01-27
> **LowSky said:**
> try VLC, it plays everthing

Yeah well one of the resons I am using linux was because of the same thing with windows nothing works. SO if I am using VLC, I might as well be using Windows:guitar:.

---

