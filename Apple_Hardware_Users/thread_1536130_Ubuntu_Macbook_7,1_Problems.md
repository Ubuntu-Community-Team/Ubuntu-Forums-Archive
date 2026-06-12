---
title: "Ubuntu Macbook 7,1 Problems"
date: 2010-07-21
forum: Apple Hardware Users
---

### Post by labaom on 2010-07-21
Firstly, I used 10.10 because that nightly build was the only one that fitted on a CD. However, I do not think it will effect my system running.

I cannot get sound to work no matter what. I followed the guide and did everything.

Also, the trackpad is real screwy. For example I am trying to move a folder. I press the folder with my thumb and try to move it around with my other finger on the trackpad. That is how I do it in Windows and Mac OSX. With Ubuntu if I click on something, the only way I can drag it is with the same finger I clicked it with. Is there a way to fix this?

Also, I am trying to install the special keyboard thingy. However, I am aware that aptitude is gone in 10.10 is there another way to install this?

Help would be appreciated! 

Thanks!!!

EDIT: Also, everytime I go in and try to search for something in synaptic package manager it closes out..

---

### Post by labaom on 2010-07-22
bump

---

### Post by theSuperman on 2010-11-04
Did you ever get your audio issues worked out? I'm having some issues with mine too...

---

### Post by labaom on 2010-11-05
Haha this is an old topic. I am not currently using Ubuntu. However, I know how to get the sound working. First of all if your using a Macbook 7,1 go here....

 [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

Go down to sound and follow the instructions. What I was confused on was it did not work after. Make sure they are all moved up. I put them down thinking the more orange the more loud.

---

### Post by theSuperman on 2010-11-05
Yeah I followed that guide. The only problem is that my left speaker sounds so much less underpowered than my right one. The right one has more bass to it. I have fooled around with alsamixer but nothing in there can fix that. I thought maybe it wasnt working properly because its a MacbookPro 7,1 guide, and I have a Macbook 7,1.

---

### Post by labaom on 2010-11-06
Macbook Pro/ Macbook is the same thing. I have the same machine you do. Make sure surrond is checkmarked. That is why it is not sounding good. Make sure everything is all the way up too.

---

### Post by blueridgedog on 2010-11-07
I just did a clean install on my new mac and documented it here:

[http://ubuntuforums.org/showthread.php?t=1613271](http://ubuntuforums.org/showthread.php?t=1613271)

Sound:

-Add the line in /etc/modprobe.d/alsa-base.conf and restart
-Run alsamixer and select from speakers and press M to unmute, then arrow up the volume.

---

### Post by theSuperman on 2010-11-09
Yeah I have played around a lot with Alsamixer, but nothing that I do makes the left speaker sound more powerful. Like I click on "Test Speakers," and the left one is somewhat quiet and the right one is nice and loud with bass.

---

