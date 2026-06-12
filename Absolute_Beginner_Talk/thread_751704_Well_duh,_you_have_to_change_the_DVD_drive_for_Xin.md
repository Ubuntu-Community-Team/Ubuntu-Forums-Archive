---
title: "Well duh, you have to change the DVD drive for Xine to work"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-10
Finally got Xine to work and quite nicely I might add in playing DVDs. 

I eventually figured out it wasn't finding my DVD drive so I went into /home/SlappyPappy/.xine directory and found a config file. Changed the third line to what you see here and uncovered it.

# device used for DVD playback
# string, default: /dev/dvd
media.dvd.device:/media/cdrom0

Now I'm a DVD watching fool in xine. I now have gxine, xine, totem, vlc, and mplayer playing dvds. Mplayer seems to be the weakest of them all. It can't play all disks. These are not rips but store bought disks. Weird.

Another day and I learned some more about Ubuntu.  :)

How many DVD players does a person need?   :lolflag:

---

### Post by kvk on 2008-04-11
OKay~

I'm still new to the directory structure of Linux, and I haven't been able to play any DVDs on my computer for a year now. I switched out the CD/DVD drive, and that allowed me to play CDs, but still no DVD. The computer is about six years old, but I'm assuming that's no issue.

So...I'm trying to find the VLC config file, and can't even find the VCL directory. Although it makes me feel like a dork- how do I find it?!?!  :)

(p.s. pretend I'm veeeeery slow and use small words....)

---

### Post by hellblade on 2008-04-13
You need to install libdvdread3 and libdvdcss2.

**libdvdread3**
In a console run:
```
sudo aptitude install libdvdread3
```

**libdvdcss2**
This is not in the official repositories because of some patents but you can download it from an other source. Again in the console run the following two commands:
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

---

### Post by linuxlizard on 2008-04-13
Someone a little more comfortable with a gui than editing a text file can make those changes in xine itself- just open xine, right click on the "screen" window, choose settings-setup then select the media tab and there you are.

---

### Post by hellblade on 2008-04-13
mistake. misinterpreted the above post as a reply to me.

---

### Post by kvk on 2008-04-16
Thanks, LL! I made a few other changes, along with that one, and got things to run. 

I'm still looking forward to the day when I don't have to use the GUI for anything! :-p

---

