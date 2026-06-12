---
title: "Firefox crashes after installing adobe flash [Resolved]"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by denysy1 on 2007-04-10
Hi,

I've tried installing flash plug-in, but it wouldn't install from add/remove programs. So I tried to do it manually. Now firefox keeps crashing. I tried reinstalling everything by searching 'firefox' in the synaptic manager, and marking everything already installed for re-installation. I also removed the flash plug-in. But firefox still keep crashing. Is there a way to fix this or somehow completely reinstall firefox (without reinstalling xubuntu, because I finally got Beryl working after many many hours of failed attempts and research).

---

### Post by GuitarHero on 2007-04-10
In synaptic, you can completely remove firefox.  Do that then either install firefox from the mozilla site or just get it from the repositories again.  Then try installing flash.  There should be many how-tos on the forums.  Search.

---

### Post by aysiu on 2007-04-10
**Actually troubleshoot the problem**
First of all, when you say "I tried to do it manually," can you detail the *exact* steps you took to do so?

Secondly, can you launch the command ```
firefox
``` from [the terminal](http://www.psychocats.net/ubuntu/terminal) and copy and paste back here any errors that appear?

**Just start fresh and remove the problem**
First, [get a fresh Firefox profile](http://ubuntuforums.org/showthread.php?t=103930&highlight=firefox+corrupt+profile)

Second, [install Flash in a clean fashion](http://www.psychocats.net/ubuntu/flash).

---

### Post by denysy1 on 2007-04-11
I tried to install falsh by doing the following:

```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -zxvf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
./flashplayer-installer 

```

When I launch firefox, by clicking the icon or through the terminal, it starts fine. It will even go on google, but as soon as I enter some website with anything other then basic html, even such as ubuntu forums, it crashes. I tried the fresh firefox profile thing, and it did not work.

If I try to remove firefox in synaptic, it says that it will also have to remove the dependancies

gnome-app-install
gxine
xubuntu-desktop

Can those be easily reinstalled if removed?

---

### Post by aysiu on 2007-04-11
Any package can be reinstalled if removed. Let's go back a second here.

You say it crashes even if you launch it from the terminal. Are there any errors when it crashes? If so, can you post them here?

And please try this, too, not just the fresh profile thing:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by denysy1 on 2007-04-11
Ok, following [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) workerd perfectly, thanks.

---

### Post by hjmf on 2007-04-11
Instead of installing it yourself directly from macromedia.com, you should consider to install the flashplugin-nonfree ubuntu package. 

If the problem persists fill up a bug report to [https://bugs.launchpad.net/ubuntu/+source/firefox/+filebug](https://bugs.launchpad.net/ubuntu/+source/firefox/+filebug)

---

### Post by aysiu on 2007-04-11
> **denysy1 said:**
> Ok, following [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) workerd perfectly, thanks.
Glad it worked out.

---

