---
title: "HOW TO: Flash"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-12-08
Right...this is my first how to, so somebody please correct me if I'm wrong :)

I've noticed that running ```
sudo apt-get install flashplugin-nonfree
``` currently doesn't work, but still reports that flash is installed...which I think is annoying for a lot of users.

So here's what I did to get flash working on my install :)

NOTE: I would recommend having java installed as well, there is an official java package in the repository's I believe

1) Open Firefox (or Opera etc.) and navigate to [www.youtube.com]("http://www.youtube.com")
2) Then try to play any video on the site
3) You will get an error message saying you do not have the latest flash player, this will also give a link to the latest version on the adobe website.
4) Click that link, and then download the .tar.bz2 file and follow those instructions (which I will go through next).

**_After downloading the .tar.bz2 file_**

NOTE: I can't remember the exact file name, but obviously you'll have it there anyway :)

Assuming the file is on your desktop:

1) Right click the file and choose extract here
2) Open a terminal and run ```
 cd ~/Desktop/flash_player_installer/
```
3) Then run ```
sudo ./flash_player_installer
```
4) The installer will ask you to close apps, and then ask where your browser is installed.
Assuming you are installing this for Firefox, when it does ask, the default location is /usr/lib/firefox



And that's it...I hope this helps, and that it works...if not then I'm sorry :p And feel free to correct me if this is wrong in places :)

**EDIT:** I am aware that this is a bug, and I'm hoping that there's an update for Gutsy at some point soon :)

---

### Post by -grubby on 2007-12-08
or you could just visit a flash site (with firefox).......
EDIT: nevermind I somehow skipped the last paragraph, it's a good howto

---

### Post by daradib on 2007-12-09
See [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

---

