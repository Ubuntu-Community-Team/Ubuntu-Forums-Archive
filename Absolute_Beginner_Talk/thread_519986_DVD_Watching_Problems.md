---
title: "DVD Watching Problems"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Holmes89 on 2007-08-07
I have VLC And Totem and I cannot see video on either, the audio does come through. What could be my problem. (All I'm seeing on both is a black screen)

---

### Post by Kingsley on 2007-08-07
Make sure you have libdvdcss2 installed.

---

### Post by Nezing on 2007-08-07
I got my DVD's to play by installing this in Terminal:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse


Then after the package has finished installing,add this in Terminal to allow encrypted (bought) DVD's to play;


sudo /usr/share/doc/libdvdread3/install-css.sh


It worked for me. :)

---

### Post by Holmes89 on 2007-08-07
Thanks it worked!

---

### Post by cobrn1 on 2007-08-07
My (6.10) installation used to point blank refuse that video dvds were in the drive until I installed the decryption libraries, then it worked like magic...

Glad your problems been fixed - enjoy the movie!

---

