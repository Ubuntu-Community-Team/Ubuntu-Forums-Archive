---
title: "How do I install Firefox 3 beta?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by rakan21 on 2008-03-25
Here's a quick question about installing programs
I know you use Terminal
and I do these codes
sudo make install
tar xjf firefox-3.0b4.tar.bz2
cd firefox-3.0b4
make
sudo make install
and then I get this error message and its not only for Firefox but most of the programs i use. I'm new to ubuntu and i barely know ****. PS HElp

Error: make: *** No rule to make target `install'.  Stop.
root@rakan-desktop:~# tar xjf firefox-3.0b4.tar.bz2
tar: firefox-3.0b4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@rakan-desktop:~# cd firefox-3.0b4
bash: cd: firefox-3.0b4: No such file or directory
root@rakan-desktop:~# make
make: *** No targets specified and no makefile found.  Stop.
root@rakan-desktop:~# sudo make install

---

### Post by aysiu on 2008-03-25
Paste these commands in the terminal. After each line, hit Enter: ```
sudo apt-get update
sudo apt-get install libstdc++5
wget -c http://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0b4/linux-i686/en-GB/firefox-3.0b4.tar.bz2
cp -R ~/.mozilla ~/.mozilla.settings.backup
sudo tar -C /opt -jxvf firefox-3.0b4.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.unlinked
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
``` It's a variation on [these instructions](https://help.ubuntu.com/community/FirefoxNewVersion#head-a18df3338b868ce5f14336fd2ee58ce6b5d574b2).

---

### Post by rakan21 on 2008-05-19
Thanks for the support

---

