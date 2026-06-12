---
title: "Cannot play DVD's"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by john262 on 2007-11-03
I am running Gutsy. I installed the Ubuntu-restricted-extras, the libdvdcss2 package, and the regionset package. But I still can't play DVD's. With some I get sound only and with other DVD's I get nothing. I also can't play DVD's that I burned with my Windows XP machine.

Does anyone know if I'm missing something? Thanks.

---

### Post by Locutus_of_Borg on 2007-11-03
try this?

[http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/](http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/)

---

### Post by john262 on 2007-11-03
Thanks. I tried it but it didn't help.

---

### Post by wesley_of_course on 2007-11-03
Under  ;  Applications ; Add / Remove ;  GStreamer Extra Plugins  

  are they installed ? Hope this helps . Good Luck

---

### Post by skymera on 2007-11-03
im guessing you might need a codec/s

some arent allowed to be downloaded by law like win32 etc,
but at the end of the day,
who give a sh..

---

### Post by noorez on 2007-11-03
I used the way that was given by Medibuntu to get dvd's to work.
Use totem-xine for the player:
This is what I did for the Fiesty release and it worked great.

install these pakages:

libdvdread3
libxine1-ffmpeg

For libdvdcss2, you need the Medibuntu repos. Add them like this:

# wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

# wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

# apt-get install libdvdcss2

---

### Post by john262 on 2007-11-04
Thanks, but I have already installed all of those things. Also, I forgot to mention that before I upgraded to Gutsy I could play DVD's, but now I can't.

---

