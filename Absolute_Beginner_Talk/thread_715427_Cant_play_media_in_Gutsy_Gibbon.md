---
title: "Cant play media in Gutsy Gibbon"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by mrdosa on 2008-03-04
I am a newbie to Linux. Using Ubuntu 7.10. Every thing was fine, but now I am not able to play any media files. When I double click any movie, VLC starts, but there is no sound, and in some time it freezes [turns grey] When I tried using command line, here is the error I got:

mahi@mahi-ubuntu:~$ vlc "Snow White and The Seven Dwarfs.avi"
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Snow White and The Seven Dwarfs.avi
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000291] main input error: no suitable access module for `Snow White and The Seven Dwarfs.avi'
[00000282] main playlist: nothing to play
[00000282] main playlist: stopping playback


I could earlier play these movies!! Can some one help.:(

---

### Post by sanddgroper on 2008-03-04
Hi
It would appear you dont have the codec's installed to play the DVD.
Have you upgraded anything lately.

Cheers
Sandy

---

### Post by mrdosa on 2008-03-04
I have not done anything other than install Avast home AV. 
Even Totem player isnt working now.

---

### Post by mrdosa on 2008-03-04
BTW it isnt a DVD I am trying to play. A 700 mb AVI file, which I could play untill yesterday! :(

---

### Post by JoshuaRL on 2008-03-04
If you cant play media in other players its probably the codecs.

Can you go into Synaptic and reinstall ubuntu-restricted-extras?

---

### Post by mrdosa on 2008-03-04
@Joshua

Can you just let me know, how I can do that?

---

### Post by JoshuaRL on 2008-03-04
Yeah, go to System->Administration->Synaptic Package Manager.

Then search for "restricted" and check for reinstallation.

Then hit Apply and let it do its thing.

---

### Post by mrdosa on 2008-03-04
Thanks, but when I searched for restricted, I got a huge list. Now which one should I reinstall!?

---

### Post by crjackson on 2008-03-04
> **mahender.mandala said:**
> Thanks, but when I searched for restricted, I got a huge list. Now which one should I reinstall!?

Install Ubuntu Restricted Extras

---

### Post by JoshuaRL on 2008-03-04
The package name is:
```

ubuntu-restricted-extras

```

---

### Post by crjackson on 2008-03-04
Also do this:

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

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

### Post by mrdosa on 2008-03-04
I am installing restricted ubuntu. Lets see...I will let you know in some time.

---

### Post by mrdosa on 2008-03-04
I have done all the steps above. And still the same thing is happening!!!

Here:


mahi@mahi-ubuntu:~$ vlc "Snow White and The Seven Dwarfs.avi"
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat Snow White and The Seven Dwarfs.avi
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000291] main input error: no suitable access module for `Snow White and The Seven Dwarfs.avi'
[00000282] main playlist: nothing to play

---

### Post by crjackson on 2008-03-04
> **mahender.mandala said:**
> I have done all the steps above. And still the same thing is happening!!!

Here:


mahi@mahi-ubuntu:~$ vlc "Snow White and The Seven Dwarfs.avi"
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat Snow White and The Seven Dwarfs.avi
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000291] main input error: no suitable access module for `Snow White and The Seven Dwarfs.avi'
[00000282] main playlist: nothing to play

Did you cut / paste from the post above?  If yes, then try to open the file with a different player.

---

### Post by crjackson on 2008-03-04
I would use nautilus to navigate to the file and right click on the file, it will present you with a list of programs to open the file with.  Chose your program from there and see what happens.

From the looks of your post, it can't even find the file.  i.e. you moved it to another location or folder but it's not there...  OR you didn't type the file name in the terminal correctly... That's what it looks like anyway...

---

### Post by mrdosa on 2008-03-04
No. nothing is working. Infact, every thing has just frozen over. i am not able to kill those applications too!!! 



I am running late to to college, I really thank you guys.,..but nothing seems to be working. I will be back in 3 hours. I hope someone finds a solution!!

---

### Post by mrdosa on 2008-03-04
I am double clicking the files to open. VLC just freezes, and none other players start too!!! Thanks for the help. Its still not working

---

### Post by crjackson on 2008-03-04
> **mahender.mandala said:**
> No. nothing is working. Infact, every thing has just frozen over. i am not able to kill those applications too!!! 



I am running late to to college, I really thank you guys.,..but nothing seems to be working. I will be back in 3 hours. I hope someone finds a solution!!

Okay, hit the ctrl+alt+backspace keys and log back in.  Make sure you installed everything I listed aboove.  Then locate the file using your nautilus file manager and try again from a clean start.  I won't be here in 3 hours, I'm at work right now.  Perhaps it will work when you try the above after you get back.

---

### Post by crjackson on 2008-03-04
Alright you posted while I was typing.  We'll get it figured out when you get back.  DON'T BE LATE FOR CLASS!!!  :)

---

### Post by mrdosa on 2008-03-05
Hi! I am back, I have the same problem even now. Is there any way, I can send you more information regarding the problem [logs etc] so that you guys can help me out?:(

---

### Post by mrdosa on 2008-03-05
Hey...I have reinstalled ubuntu...its working now

---

