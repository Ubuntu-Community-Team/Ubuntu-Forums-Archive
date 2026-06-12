---
title: "dvd difficulties"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by epmcauley on 2008-03-17
I am completely new to ubuntu and am in general quite useless with computers and technology. I have been having difficulties getting my dvd player to work. I have both vlc and gxine. I can get my dvds to load in gxine but they skip and jump and dont run smoothly and the video playblack is a greenish colour. Sorry for the lack of technical explanations but I hope somebody understands and can hep??? I would be very grateful

---

### Post by kamitsukai on 2008-03-17
Do they play properly in vlc? and do you have the drivers for your graphics card installed?

---

### Post by jan quark on 2008-03-17
run this in terminal

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
```

sudo /usr/share/doc/libdvdread3/install-css.sh
```

and try to open the dvd with gxine once again

---

### Post by billgoldberg on 2008-03-17
You need to download vlc from the medibuntu repository or install libdvdcss2 from the same repo.

The vlc version in the standard repositories won't play dvd's.

[link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

---

### Post by epmcauley on 2008-03-18
thanks Jan thats fixed...boredom be gone!!!!! thanks for the help  guys

---

### Post by diilbert on 2008-03-21
> **epmcauley said:**
> I am completely new to ubuntu and am in general quite useless with computers and technology. I have been having difficulties getting my dvd player to work. I have both vlc and gxine. I can get my dvds to load in gxine but they skip and jump and dont run smoothly and the video playblack is a greenish colour. Sorry for the lack of technical explanations but I hope somebody understands and can hep??? I would be very grateful

I had a similar problem with my laptop and I just fixed it with the Contrast setting in Gxine.  Looks good now.

---

