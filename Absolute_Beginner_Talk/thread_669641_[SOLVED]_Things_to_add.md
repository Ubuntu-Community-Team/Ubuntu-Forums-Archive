---
title: "[SOLVED] Things to add"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-16
Hey, I have just recently started using Gutsy 7.10 and I love it! I still use Windows for things like iTunes and DivX Movies because I find they are easier to use on Windows. But I am now past the "brand new OS" stage and I have come here to see if anyone can suggest something to spice Ubuntu up a bit. Not that I've got bored or are thinking of switching back to Windows (god forbid).

Thanks, Fraser.

---

### Post by PeterJS on 2008-01-16
Have you looked at Amarok for managing music and ipod support? As for DivX movies, how about VLC, it works the same on pretty much all platforms, which is really well.

---

### Post by jan quark on 2008-01-16
fraser from scottland

welcome to the Ubuntu community, 
but please use this section of the forum to ask question about "serious":) problems

The section Experiences and Testimonials should be fine.

By the way what do you mean by spicing up?

Adding Eye-Candy?
or application?

---

### Post by Fraser from Scotland on 2008-01-16
Hey, sorry i wasnt too sure where to post this thread. Em, well I've been looking at other threads and I like the look of conky, except im not sure what it is lol. All i know is you can get some sort of info pane at the side. Like this one  [http://ubuntuforums.org/attachment.php?attachmentid=17956&d=1161470797](http://ubuntuforums.org/attachment.php?attachmentid=17956&d=1161470797)

---

### Post by nikoPSK on 2008-01-16
for playing dvd's in totem in gutsy:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus.

Hope that helps,
Niko

---

### Post by Fraser from Scotland on 2008-01-16
thanks alot guys :) ill look into conky. I'll mark this as solved.

---

