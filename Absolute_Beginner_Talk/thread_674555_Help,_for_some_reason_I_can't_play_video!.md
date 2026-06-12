---
title: "Help, for some reason I can't play video!"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by kanati on 2008-01-21
My video playback was working perfectly.  Then I tried to install QDVDAuthor which worked for a while and then started crashing so I removed it.  Since then I haven't been able to play movies of any type using any program.  Totem crashes as soon as it loads the movie, VLC plays a scrambled version, as does Miro.  This doesn't make any sense, what's going on?

PS, I just realized that QDVDAuthor is meant for KDE, not gnome.  Might that have screwed something up?

Ubuntu Version 7.10

Thanks for any help

Edit <Ignore this and see below>

---

### Post by billgoldberg on 2008-01-22
Try reinstalling your video codecs. (gstreamer or xine, whatever you use).

Also try this in a terminal:

sudo apt-get install ubuntu-restricted-extras

This **might** help.

---

### Post by kanati on 2008-01-22
thanks, reinstalling gstreamer got my video working again...sort of

now all my videos play in a weird blue colour cast, it's like I'm looking at it through a strong blue filter 

any ideas?

---

### Post by crjackson on 2008-01-22
> **kanati said:**
> thanks, reinstalling gstreamer got my video working again...sort of

now all my videos play in a weird blue colour cast, it's like I'm looking at it through a strong blue filter 

any ideas?

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by kanati on 2008-01-23
hmmm....
  i ran those lines of code and now I'm back to where I was before, all the xine based players crash as soon as I try to open a video and VLC plays a scrambled version of the video

---

### Post by kanati on 2008-01-23
it's like xine doesn't work and Gstreamer has colour issues

---

