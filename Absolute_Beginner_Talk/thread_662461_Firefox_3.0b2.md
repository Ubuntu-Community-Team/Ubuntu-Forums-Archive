---
title: "Firefox 3.0b2"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by defaultuser01 on 2008-01-09
Can someone please help me remove FF 3.0b2 and undo whatever is keeping me from using FF 2... I used these instructions...

"> Installing Firefox3.0 beta2 in ubuntu

Preparing your system

sudo apt-get install libstdc++5

Now you need to take backup of your old firefox prferences

sudo cp -R ~/.mozilla ~/.mozillabackup

Now you need to download firefox 3.0b2 from here

Now you have firefox-3.0b2.tar.bz2 file

Unzip the .tar.bz2 file in /opt directory using the following command

sudo tar -C /opt -jxvf firefox-3.0b2.tar.bz2

Now you need to link the plugins using the following command

cd /opt/firefox/plugins/

sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

Now you need to create a link to your new firefox launcher using the following command

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox

sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

This will complete the installation of firefox 3.0b2

If you want to open firefox 3 beta 2 go to Applications—>Internet—>Firefox Web Browser"
I did exactly as it says.

---

### Post by PurposeOfReason on 2008-01-09
First, what is wrong with the beta? I'm pretty sure everything installed is in synaptic so you should be able to go under synaptic and remove it.

---

### Post by defaultuser01 on 2008-01-09
The beta freezes for long periods of time and pages using java dont seem to work correctly or dont work at all. I tried using synaptic to remove, and it does remove firefox 2.?? but leaves the beta. It looks like i have installed it beside FF2. I think I have replaced the link to point to FF3 instead of FF2.

---

### Post by defaultuser01 on 2008-01-09
I think my problem is somewhere in this.

> Now you need to create a link to your new firefox launcher using the following command

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox

sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

This will complete the installation of firefox 3.0b2


 I don't know how to change this back.

---

### Post by ametade on 2008-01-10
You can remove firefox 3 beta2 using the following commands:
```

sudo rm /usr/bin/firefox.ubuntu
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox.ubuntu
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox

```
Then you can reinstall Firefox 2 from synaptics.

---

### Post by philinux on 2008-01-10
And I was wondering about installing it. :)

---

