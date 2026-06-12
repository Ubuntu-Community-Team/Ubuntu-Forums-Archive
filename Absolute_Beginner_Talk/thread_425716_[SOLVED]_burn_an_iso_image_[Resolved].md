---
title: "[SOLVED] burn an iso image [Resolved]"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by johnnylong on 2007-04-27
Hi Boyz & Girlz,
   Just wanted to let everyone know that Windows is dead, Long Live Linux! The new version of Ubuntu (version 7) is out and I would like to burn an iso image just in case the need to reload my system arises. What software does anyone know of that might help me with my task? The other problem I have had is dvd movie playback. Totem is a total waste of time. I have download every piece of software connected to totem and to date have not been able to play back any type of movie. I haven't minded giving up Windows and have no intentions of going back, but if there is a way to playback dvd's I'd appreciate some help (I have a collection of over 700 and would like to take advantage of them when I'm away from home.. HELP!!). 
Till next time... Thanks!

---

### Post by Najand on 2007-04-27
If you are using GNOME, just right clicking on the iso file will give you the option to "write to disk"

---

### Post by aysiu on 2007-04-27
VLC is a great DVD player.

---

### Post by Maxtine on 2007-04-27
For information on burning the iso try 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  [http://doc.ubuntu.com/screencasts/Do..._an_Ubuntu_ISO](http://doc.ubuntu.com/screencasts/Do..._an_Ubuntu_ISO)

700 dvd's wow  you might try mplayer and check out the multimedia section [http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)
:lolflag:

---

### Post by deadgobby on 2007-04-27
You can install k3b in synaptic. K3B rocks and your can burn just about any thing.
 Have you installed the restricted formates to able to play DVD's?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Gobby

---

### Post by oilchangeguy on 2007-04-27
700+ dvd's????????? how do you choose what to take with you? did you know if you are a netflix subscriber you can watch movies online free. this is in addition to what you are able to get in the mail.

---

### Post by rumli on 2007-05-01
Here are 4 simple lines to get Totem to play almost anything, including DVD, mp3, wma, wmv, mov, etc.:

```

wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb
sudo dpkg -i /tmp/w32codecs_20061022-0.0_i386.deb /tmp/libdvdcss2_1.2.9-0.0_i386.deb
sudo apt-get install totem-xine libxine-extracodecs

```

See [here]("http://www.cs.cornell.edu/~djm/ubuntu/#multimedia") for more info.

Edit: To burn audio, data, and ISOs to CD and DVD, I use Gnomebaker.
```

sudo apt-get install gnomebaker

```

---

### Post by johnnylong on 2007-05-04
Thanks all. Install gnome-baker and got the needed results, Ubuntu Rulez!! 
Hack the Planet!!!!

---

