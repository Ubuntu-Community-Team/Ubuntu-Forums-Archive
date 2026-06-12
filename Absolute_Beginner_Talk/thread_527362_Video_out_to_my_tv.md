---
title: "Video out to my tv?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by MonuMan5 on 2007-08-16
I have a video out on my pc.  When I used to use windows xp, I was able to add the tv to my computer like it was an addition to my desktop.  

I would like to do this using Linux.  It doesn't have to be an extension of my desktop, if it is a clone, that would be ok.  But I do want to get video from my computer to my television.  

What program would I use?  How would I do this?  

And please keep in mind.  I'm a noob.  (If you couldn't tell already)

---

### Post by Hobo Joe on 2007-08-16
Could you tell us your graphics card and it's ouputs?

S-video, or are you using VGA or DVI do go from your computer to your TV?

---

### Post by MonuMan5 on 2007-08-17
I have an S-Video out on my video card.  Which is a.....  Radeon X300.

---

### Post by w4ett on 2007-08-17
You might want to have a look at this how-to:

[http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1)

---

### Post by MonuMan5 on 2007-08-20
Things are about to get real noobie.  

Ok, so i type that first segment into the program Terminal  

monu@MonuMan5:~$ git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-ati
destination directory 'xf86-video-ati' already exists.
monu@MonuMan5:~$ cd xf86-video-ati
monu@MonuMan5:~/xf86-video-ati$ git checkout origin/randr-1.2
error: pathspec 'origin/randr-1.2' did not match any.
monu@MonuMan5:~/xf86-video-ati$ ./autogen.sh --prefix=/usr/
./autogen.sh: 9: autoreconf: not found
monu@MonuMan5:~/xf86-video-ati$ make
make: *** No targets specified and no makefile found.  Stop.
monu@MonuMan5:~/xf86-video-ati$ make install

What is the meaning of all of this?

---

