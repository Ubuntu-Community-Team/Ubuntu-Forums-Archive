---
title: "Totem movie player and MPG pluggins"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by phantomcct on 2006-12-28
Hi,
Just installed Ubuntu and tried to run an mpeg movie using Totem movie player.
It wouldn't play the movie and said that I do not have a decoder installed for this file.

Can anyone tell me where to get one?

Cheers 
Phantomcct

---

### Post by ibbryn on 2007-01-04
I just installed ubuntu and am very excited about it!

Got the same problem, mpg (and wmv) files can't be read using Totem.  Also wouldn't pay a commercial DVD - said I needed plug ins.  

Am searching posts, faqs, etc. for answers but I immediately found this post so I thought I'd bump it in hop of an answer.

---

### Post by ibbryn on 2007-01-04
and this thread:
[http://ubuntuforums.org/showthread.php?t=326467&highlight=mpg](http://ubuntuforums.org/showthread.php?t=326467&highlight=mpg)
seems to have a lot of info on the problem.

---

### Post by rajeev1204 on 2007-01-04
hi

install automatix from [www.getautomatix.com](www.getautomatix.com) 

It will do all u need

---

### Post by jpeddicord on 2007-01-04
All you should have to install is all of the gstreamer-plugins- packages in Synaptic. You do not need to install any plugins ending in -dev or -doc, however you can if you wish.

Also, if you are Ubuntu Edgy, here is an alternate way. Go to Applications > Add/Remove.
Scroll down the list for GStreamer Extra Plugins. Check it, and click OH. You should now be able to play the codecs.

Jacob

---

### Post by ibbryn on 2007-01-04
I thought I was good on this but it looks like Automatix is a tool you use to get plug ins and packages when you are already on line. 

This will sound weird (since I'm obviously on line) but I don't have on line access with the laptop I am configuring.  So I have to download whatever tools I need and hand carry them to the laptop I am configuring.  

So I'm going to keep looking for tools I can download and install from a CD or thumb drive.

---

### Post by rajeev1204 on 2007-01-04
hmm

Thats not the right way to install in ubuntu .

Just get ur laptop online somehow for a few minutes and install GXINE from the repositories along with **libxinemain and libxine-extracodecs**

Will play ur dvd's fine. Totem is useless and crashes all the time.

For those stupid region specific dvd's u need libdvdcss2 which is best done by automatix . 

As far as windows media video , well, mplayer from repositories will play it .If u need streaming videos , install mozilla-mplayer plugin also


Let me know.


regards

rajeev

---

### Post by kanna1620 on 2007-01-13
> **rajeev1204 said:**
> hmm

Thats not the right way to install in ubuntu .

Just get ur laptop online somehow for a few minutes and install GXINE from the repositories along with **libxinemain and libxine-extracodecs**

Will play ur dvd's fine. Totem is useless and crashes all the time.

For those stupid region specific dvd's u need libdvdcss2 which is best done by automatix .

As far as windows media video , well, mplayer from repositories will play it .If u need streaming videos , install mozilla-mplayer plugin also


Let me know.


regards

rajeev

I installed the gxine movie player and the xine movie player but those are not working porperly.
gxine is giving a very bad picture quality and the xine is abruptly exiting  playing a movie file. I dont know the reason. So please help me someone.Iam a newb to Ubuntu.Thanx for help.

---

