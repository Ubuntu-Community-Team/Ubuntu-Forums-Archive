---
title: "newbie stuck , ref: dvd playback"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by halo1968 on 2007-12-10
HI all,
      Absolute Newbie here.
tried playing a DVD in TOTEM but it says i dont have the plugins .etc.
i did a little searching on here and read  i should install 'restricted extras' ,this i have done but no luck.I also installed VLC player but no luck.
Its obvious i am doing/missing something.Please help.-MIke.

---

### Post by Ex-windows on 2007-12-10
HI,
If you are using Fiesty  this should do it
 Did you install the libdvdread3 file?
This can be done using synaptic package manager.
Then in a terinal run this command

sudo /usr/share/doc/libdvdread3/install-css.sh

Also you will need the extra codices
In the termianl again type (copy/paste) this command
sudo apt-get install totem-xine libxine-extracodecs
Then answer yes and it should install them.

If you are using the new gutsy try this page 
[https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd)
Hope this gets you going

---

### Post by halo1968 on 2007-12-10
Hey ,
       Thanks EX-WINDOWS!  all is working now thanks for the info.Also i had a duff disc drive my pc was taking for the default player i think, so i disconnected it.:)

---

### Post by halo1968 on 2007-12-10
HI,
  Just to keep you updated,Vlc Player works now but not,totem.As long as i have 1 that works it's ok.thanks again.

---

### Post by Ex-windows on 2007-12-10
Glad it is working 4 u. Never tried the vlc but
As u say as long as one is wworking that all that matters lol. Happy Holidays..
Quick edit, I think u should mark this as solved (if u haven't already). Problem is I am not sure how lol

---

### Post by warthogism on 2007-12-10
> **halo1968 said:**
> HI,
  Just to keep you updated,Vlc Player works now but not,totem.As long as i have 1 that works it's ok.thanks again.

exact same thing here.  gxine and totem wont play them, but vlc does.  thanks, though it'd be nice to figure out why.

---

### Post by Ex-windows on 2007-12-10
Yes I seen your post too and cant really understand why it wont work for either of you. I have ubuntu on all 3 comps  (Using Fiesty) and I used the same technique  (using xine) It even plays the Videos I have stored in the comp. If You like I could post the entire routine I used ( I have it saved on a text doc lol) Take care

---

