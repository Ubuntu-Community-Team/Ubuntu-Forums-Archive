---
title: "Mp3"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by hades6 on 2006-09-02
hi i just install ubuntu on my syteme and i'm trying to install amarok or any mp3 reader and it dose not seem to work. it show the disk cover and every trach info but no sound and less than 1 sec by track.
i have tryed update the codec but it is not working

---

### Post by macdo on 2006-09-02
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Welcome to Ubuntu!
May I suggest that you search the forums before you post, as you'll often find the answer without having to wait...

Cheers,

---

### Post by ron999 on 2006-09-02
Hi hades6

You have to install the codecs for mp3 players yourself.
(These are called Restricted Formats).
The info is in the link posted by macdo above.

---

### Post by hades6 on 2006-09-02
i did
$ sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs

:confused: belive me for a firt time linux... not too shure of what i done

it answers that no paquet are coresponding and my mp3 are not working

---

### Post by ron999 on 2006-09-02
hades6

I can't help much here. When I installed mine I used the program at

[http://getautomatix.com](http://getautomatix.com)

It's a program that installs codecs and other things you might need automatically.

---

### Post by macdo on 2006-09-02
First of all, you need to update your sources.list file (that's the list of all the places you will be downloading programs from). You can copy and paste these commands into a console. I'm presuming you're using Ubuntu, not kubuntu...
First, make a backup:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bckup
```
Then open the file to edit it:
```
gksudo gedit /etc/apt/sources.list
```
In that file, you need to remove every # that's in front of a line starting with 'deb'. The # comments out lines, so the program doesn't use them.
When that's done, save and close the file. 
Then, in the console, type:
```
sudo apt-get update
sudo apt-get upgrade 
```
The first command updates the program lists on your PC, and the second updates the programs themselves. 
When all that's done, you can install the mp3 codecs with the link above. 

RECOMMENDED READING: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

