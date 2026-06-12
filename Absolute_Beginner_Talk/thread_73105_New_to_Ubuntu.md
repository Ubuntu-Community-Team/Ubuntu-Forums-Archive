---
title: "New to Ubuntu"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Linoman on 2005-10-08
Hello there all. This looks like a very kind and helpful community. I just have a few questions though. I've tried many linux distros, through a period of 3 years and always been let down. Until I tried Ubuntu 5.0.4, I installed it on a P3 866MHZ. After getting it installed and getting hold of the Mp3 codec (boy that was fun) and installing KDE 3.4. I got it running pretty well but a few things still bug me:

1) I'm located in South Africa, and my repositories used to connect to.za but I changed them so I could get hold of the Mp3 codec. But now I'm having problems with the .com repositries so I would like to change it back to .za my problem is that I did not keep a back up? Anyone know the South Africa repositories?

2) Everynow and then I like to use Gnome, only thing is how on earth do I create a shortcut to another directory? So that it will show up on my desktop?

3) Whats a good Mpeg/Avi player to use? 

Ubuntu linux rules, the best distro I've ever used. Well done everyone.
Thanks

---

### Post by xmastree on 2005-10-08
[QUOTE=Linoman]2) Everynow and then I like to use Gnome, only thing is how on earth do I create a shortcut to another directory? So that it will show up on my desktop?[/quote]The easy way is to open nautilus (the file manager) find the folder you wish to make a link to on your desktop, and drag it with the **middle** button to your desktop. You'll be asked what you want to do. Move here, copy here or link here. Select link. That way the folder will still be in the same place and you'll have the equivalent of a Windows shortcut to it on the desktop.
> 3) Whats a good Mpeg/Avi player to use?gxine is pretty good, as is mplayer.

---

### Post by tehwa on 2005-10-08
1. Try this in your /etc/apt/sources.list, dont forget to backup your current list if things don't work out```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
File contents:
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://za.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://za.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://za.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://za.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://za.archive.ubuntu.com/ubuntu hoary universe
deb-src http://za.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
```
Remember to update.

3. I prefer VLC, very tidy, seems to play files that other players raise errors.

---

### Post by Linoman on 2005-10-08
Thank you everyone for your replies, the .za  repositories work like a charm. I ended up installing Kaffiene for movie files and it works like a charm. I discovered that I need an app that can play midi files? What app can I use? Also how can I take screenshots in KDE?

---

### Post by pinoyskull on 2005-10-08
ksnapshot is the app for screen capture in KDE :)

---

### Post by Gustav on 2005-10-08
[QUOTE=Linoman]Thank you everyone for your replies, the .za  repositories work like a charm. I ended up installing Kaffiene for movie files and it works like a charm. I discovered that I need an app that can play midi files? What app can I use? Also how can I take screenshots in KDE?[/QUOTE]
The easiest way to play midi files is to install timidity, freepats and perhaps pmidi

---

### Post by mips on 2005-10-12
[QUOTE=Linoman]Thank you everyone for your replies, the .za  repositories work like a charm. I ended up installing Kaffiene for movie files and it works like a charm. I discovered that I need an app that can play midi files? What app can I use? Also how can I take screenshots in KDE?[/QUOTE]

Just a little tip. Rather hash out the text you dont want than deleting things. In future if you need the text again you just remove the hash marks. Comments are also handy as to what you are doing.

cheers
mips

---

