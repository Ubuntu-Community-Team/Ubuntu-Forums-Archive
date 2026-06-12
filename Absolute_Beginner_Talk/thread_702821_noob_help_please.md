---
title: "noob help please"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by natedogg624 on 2008-02-20
alright i have a few questions:

[COLOR="Red"][COMPLETED[/COLOR]]amarok-- i installed it and tried playing mp3's said it needed the proper codec and asked if i wanted to download it so i installed it and restarted and open it up again and it says the same thing.  the notice in the bottom says to configure xine engine...  i have read in other threads to just delete the xine folder.  but i have no idea where to find it.  so if someone could help me out either guide me to it or give me a terminal command. i should also mention that i can play the same songs in the regular video.audio player.  so this is an issue with amarok/xine

i downloaded a few themes and widgets from gnome-look.com and the files are on my desktop.  how do install them? 

also i have an HP x3000 expansion dock that i use for my laptop.  I have all my connections running through there (LAN line, AC, ext. HDD, printer, other misc usb inputs) running through that to my computer.  In windows i play music and it comes out of the built in speakers in the expansion bay.  But in Ubuntu when i play music (same setup) it plays through my laptops internal speakers.  Its as if the sound is not getting through the cable that connects my laptop to the expansion dock.  yes this may be nitpicky, but its something i would like to try and figure out.

thanks!

---

### Post by DoctorMO on 2008-02-20
rm -fr ~/.xine

For all your cleaning needs, see: "ls ~/.*"

---

### Post by jan quark on 2008-02-20
this howto is very useful
[URL="http://monkeyblog.org/ubuntu/installing/"]
how to install anything in ubuntu[/URL]

---

### Post by natedogg624 on 2008-02-21
amarok wont play mp3's after repeatedly trying to install the codec it says to it still wont' work, how can i choose a different engine or make this work.

i really want to use amarok help please!

---

### Post by Joeb454 on 2008-02-21
try running the following code from a terminal (Applications>Accessories>Terminal):

```
sudo apt-get install libxine1-ffmpeg
```

You will be asked for your password (it won't show you're typing it however). Then restart amarok and try again :)

---

### Post by metallicamaster3 on 2008-02-21
If the sound isn't going to the device it is plugged into, then it is more likely a sound card/chipset issue rather than a device or wire issue. Give us the output of "lspci" in a terminal so we can potentially find a driver for you to update and/or install.

---

### Post by natedogg624 on 2008-02-21
> **Joeb454 said:**
> try running the following code from a terminal (Applications>Accessories>Terminal):

```
sudo apt-get install libxine1-ffmpeg
```

You will be asked for your password (it won't show you're typing it however). Then restart amarok and try again :)

awesome that worked! thanks a lot odd though i could have sworn i installed that package already...

thanks for your help!

---

### Post by Joeb454 on 2008-02-22
No problem :) glad you can hear your music now ;)

---

### Post by billgoldberg on 2008-02-22
Just for future readers of this post with the same problem.

If you add the medibuntu repo, and then download amarok using synaptic, add/remove, apt-get or aptitude you will have mp3 support by default.

That repo also gives you vlc with all the features (not like the one in the standard repo) and lots of other things like xmms-wma support, dvd support, skype, google earth, ...

[How to add the medibuntu repo.]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

---

