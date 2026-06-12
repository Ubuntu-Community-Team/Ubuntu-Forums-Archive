---
title: "wmv files in Xubuntu 6.06"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-12-22
What packages do I need to install on Xubuntu 6.06 to play wmv files?  I've got them playing on my other machine with Totem but I'm staying away from Gnome dependencies because this machine is old and slow.  I've got VLC installed but the videos aren't working.  What packages do I need to install to get them to work?

---

### Post by RomeReactor on 2007-12-22
Hi. Due to [patent and copyright issues]("https://help.ubuntu.com/community/RestrictedFormats"), it's up to you to decide whether to install the following package:
```
sudo apt-get install ubuntu-restricted-extras
```

After that, you should be able to play most media. If you're still unable to play wmv files, you may need to add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

And then install the w32codecs package:
```
sudo apt-get install w32codecs
```
If your Ubuntu is 64 bit, then the package is w64codecs. If you have doubts or questions, please post back.

---

