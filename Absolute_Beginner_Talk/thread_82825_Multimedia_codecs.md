---
title: "Multimedia codecs"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by commodore on 2005-10-27
I want to install multimedia codecs, i got this from ubuntuguide:
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

Is it safe? Because when I tried to do that last time my system was so messed up I had to reinstall.

---

### Post by JurB on 2005-10-27
The ubuntuguide for 5.10 in Gnome (System -> Help -> Ubuntu 5.10 starter guide -> Applications -> Music and Movies) explains it some what differently, i did it that way and had no complaints:

1. Enable Universe and Multiverse

2. In Synaptic:
Libraries (multiverse) > gstreamer0.8-plugins-multiverse
Libraries (universe) > gstreamer0.8-plugins
Libraries (universe) > gstreamer0.8-ffmpeg
Libraries (universe) > gstreamer0.8-mad
Multimedia > vorbis-tools
Multimedia (multiverse) > lame
Multimedia (multiverse) > faad
Multimedia (multiverse) > gstreamer0.8-lame
Multimedia (universe) > sox
Graphics (multiverse) > mjpegtools
Graphics (universe) > ffmpeg 
GNOME Desktop Enviroment (universe) > totem-xine

3.Register G-streamer in terminal type:
gst-register-0.8

---

### Post by commodore on 2005-10-27
Can't do it, that ee.archive.ubuntu.com thing isn't working.

---

### Post by JurB on 2005-10-27
What exactly can't you do?

---

### Post by commodore on 2005-10-27
I can't see library(multiverse), probably because synaptic can't find stuff from ee.archive.ubuntu.com.

---

### Post by commodore on 2005-10-28
The thread is olding, can someone help me please?

---

### Post by JurB on 2005-10-28
Wait did you add Universe and Multivers as explained [here]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse")?

---

### Post by commodore on 2005-10-29
Yea, I think so.

---

### Post by JurB on 2005-10-29
I think your countrie's repo server is down.
I don't know to much about it, but i think wich server you use is assigned on install, probably the closest to your location.
There must be another way to get those packages tough (from another server close to you).
I think you'll get better support on this issue in the "Ubuntu repository support" section of the forum. 
Try to give exact discriptions on the errors you get tough.

Hope this helps.

---

### Post by aysiu on 2005-10-29
Follow these directions exactly: [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by commodore on 2005-10-30
That doesn't work either. It seems that it gives even more errors:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Mustard on 2005-10-30
Can you type in terminal..

```
sudo gedit /etc/apt/sources.list
```

and then copy and paste its contents in here plz?

---

### Post by commodore on 2005-10-30
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ee.archive.ubuntu.com/ubuntu](http://ee.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by Mustard on 2005-10-30
commodore, use the sudo gedit /etc/apt/sources.list command to open up that file again.. and go to all the entries that start with 'ee.' and remove the 'ee.' from each of them.  Save and try again.

---

### Post by commodore on 2005-11-02
Sorry for not replying for so long time. I've been very busy.

This didn't work either, it gave me this error:
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Mustard on 2005-11-02
Hmmm...it's a bit hard to troubleshoot at this pace.  It's going to take too long.

My suggestion would be to use the IRC support channel, where you can get more real-time support.

Ubuntu comes with the x-chat client for IRC.  Try opening that and look for the Ubuntu server and connect to that.  It should automatically join channel #ubuntu and you can seek some help in that support channel.  If you want to manually configure another IRC client the relevant information is...

Server: irc.freenode.net
Channel: #ubuntu

Here is a list of all the other support channels available;
[https://wiki.ubuntu.com/InternetRelayChat?action=show&redirect=IrcChannels]("https://wiki.ubuntu.com/InternetRelayChat?action=show&redirect=IrcChannels")

---

### Post by ecobuntu on 2005-11-02
Change ee to us or ca

---

### Post by ecobuntu on 2005-11-02
change ee to us or ca

---

### Post by commodore on 2005-11-05
Didn't work again :D

---

### Post by commodore on 2005-11-05
Ok, I finally got it fixed.

---

### Post by JurB on 2005-11-05
Can you explain how you solved it?
It might help others.

---

### Post by commodore on 2005-11-05
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

