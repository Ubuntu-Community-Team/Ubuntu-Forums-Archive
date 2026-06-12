---
title: "How Do I get A DVD To Work?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Gigidy5 on 2007-10-25
How?

---

### Post by Buried:. on 2007-10-25
um Try Insterting it. maybe your CD/DVD driver is not supported in Ubuntu

---

### Post by magicman5421 on 2007-10-25
run movie player, put ur disk in, if you don't already have the drivers, movie player will prompt you to install them. easy from there.

---

### Post by PointyWombat on 2007-10-25
you can also run:

# dmesg

view the output and note any references to your CD/DVD drive. There should be mention of which driver it has loaded for it.

Also, cat out /proc/sys/dev/cdrom/info to see capabilities of it.

---

### Post by Gigidy5 on 2007-10-25
K... So It all goes fine. But then It displays "Cannot Read From Source"



What do I do?



Where Do I Get The Plug-ins?

---

### Post by rudeboyskunk on 2007-10-25
you most likely need to install "libdvdcss."  It is a package that is not legal in some countries, as it breaks the encryption that comes with most DVDs. Before you try it though, do a search for "libdvdcss" in Synaptic and install libdvdread3.  See if that works first.  If not, download and install libdvdcss.   [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

---

### Post by Incense on 2007-10-25
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Follow the guide on that page and you'll be set to play encrypted DVD's in the normal movie player.

---

### Post by Gigidy5 on 2007-10-26
Sorry neither works>>>.

---

### Post by meborc on 2007-10-26
try vlc player... just install vlc```
sudo apt-get install vlc
```then file>open disk>dvd

---

### Post by Dr Small on 2007-10-26
VLC player will play most formats out of the box, so I would try it, as meborc recommended.
Then I setup VLC player as my default player for DVDs under System > Preferences > Removable Drives and Media, and just have VLC player open DVDs :D

Dr Small

---

### Post by stchman on 2007-10-26
> **Gigidy5 said:**
> How?

Are you referring to playing a encrypted Hollywood DVD.  Yes, you can do that.

      Ubuntu 6.06 "Dapper Drake":

      ```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```

      Ubuntu 6.10 "Edgy Eft":

      ```
sudo wget http://www.medibuntu.org/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list
```

      Ubuntu 7.04 "Feisty Fawn":

     ```
 sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

      Ubuntu 7.10 "Gutsy Gibbon":

      ```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

      Then, add the GPG Key:

      ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Install the CSS decoder from Medibuntu
```
sudo apt-get install libdvdcss2
```


I recommend vlc as your media player.

```
sudo apt-get install vlc
```

You should now be able to play encrypted Hollywood DVDs.

---

### Post by roschell on 2007-11-04
Try few DVDs as there might be an error on the disc and therefore it can not read it. There is a difference between reading a dics and playing it. 

The system may be able to read the disc does not mean it will play it without having the needed codecs, but if it does not read > it will definitely not play. It seems you approaching first the stage to try to read it.

---

