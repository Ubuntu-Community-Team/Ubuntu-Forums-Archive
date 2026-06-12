---
title: "[SOLVED] Help with libdvdcss"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by ertrules22 on 2007-08-06
Okay, I have a Dell latitude D600 with Ubuntu 7.04 Feisty Fawn on it.  It has a dvd player, and I have Totem Movie Player, and Ogle on it.  I have the libdvdcss-1.2.9.tar.gz on my desktop and I need to know how to build/make/install or whatever I need to do.  I just want to play a DVD on my laptop, but it says something along the lines of the file format cannot be played, error something or other, I will update when I have a dvd in it (I am at work right now!).  Any help would be appreciated.  I have already read the readme, and I am kind of new at this, so I don't exactly know how to do this.
Thanks,
ertrules22

---

### Post by por100pre1 on 2007-08-06
An easier way would be to visit [www.medibuntu.org]("http://www.medibuntu.org"), add the repositories, and install the codec with Synaptic.

---

### Post by steve.horsley on 2007-08-06
The usual thing is to unzip it, change to the directory it creates and then run these 3 commands:
[B]./configure
make
sudo make install[/B]

but it might be easier to downoad and just double-click the .deb installer from here:
[http://freshmeat.net/projects/libdvdcss/](http://freshmeat.net/projects/libdvdcss/)

P.S.
medibuntu - nice link - I didn't know about that one.

---

### Post by Inxsible on 2007-08-06
> **ertrules22 said:**
> Okay, I have a Dell latitude D600 with Ubuntu 7.04 Feisty Fawn on it.  It has a dvd player, and I have Totem Movie Player, and Ogle on it.  I have the libdvdcss-1.2.9.tar.gz on my desktop and I need to know how to build/make/install or whatever I need to do.  I just want to play a DVD on my laptop, but it says something along the lines of the file format cannot be played, error something or other, I will update when I have a dvd in it (I am at work right now!).  Any help would be appreciated.  I have already read the readme, and I am kind of new at this, so I don't exactly know how to do this.
Thanks,
ertrules22

```
tar xvzf libdvdcss-1.2.9.tar.gz 
```Navigate to the extracted directory and
```

./configure
sudo make install

```

EDIT : Got beat :rolleyes:

---

### Post by jvc26 on 2007-08-06
I'd go into terminal:

Applications -> Accessories -> Terminal

And type:
```

sudo apt-get install libdvdread3 libxine1-ffmpeg libdvdcss2 totem-xine

```

Note: You need multiverse and Universe repos available, see [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories").
Il

---

### Post by PriceChild on 2007-08-06
Click the following link and let gdebi install it for you.
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2%2bb1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2%2bb1_i386.deb)

---

### Post by ertrules22 on 2007-08-06
I haven't tried it out yet, but I just did the suggestion from PriceChild, and it seemed to work, so I will let you all know what the outcome is when I get home and have access to a DVD.  Thanks for all your help!
:guitar::)

---

### Post by ertrules22 on 2007-08-07
Good news!  I got home, stuck a DVD in the drive, and ran ogle, and it worked perfectly (although it didn't work in Totem, oh well, I will use Ogle!)  Well, jolly good then.
Tally Ho!
ertrules22:lolflag:

---

### Post by stchman on 2007-08-07
> **ertrules22 said:**
> Okay, I have a Dell latitude D600 with Ubuntu 7.04 Feisty Fawn on it.  It has a dvd player, and I have Totem Movie Player, and Ogle on it.  I have the libdvdcss-1.2.9.tar.gz on my desktop and I need to know how to build/make/install or whatever I need to do.  I just want to play a DVD on my laptop, but it says something along the lines of the file format cannot be played, error something or other, I will update when I have a dvd in it (I am at work right now!).  Any help would be appreciated.  I have already read the readme, and I am kind of new at this, so I don't exactly know how to do this.
Thanks,
ertrules22

Follow my procedure and you will be watching encrypted DVDs in no time.  I recommend VLC over Totem for DVD viewing.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

