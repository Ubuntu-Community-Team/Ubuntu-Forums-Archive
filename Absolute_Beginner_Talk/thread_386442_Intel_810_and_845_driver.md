---
title: "Intel 810 and 845 driver"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-03-17
HI Every1.
I had ordered some UBuntu Shipit CDs and distributed them among my friends. Two of them do not have an internet connection and they have onboard graphic cards of intel (810 and 845 respecively). Now what i would like to know is , how to install graphic drivers on their systems (please reember without internet!!) and how to check if the drivers are insatlled properly. Also , they want to play Counter Strike in OpenGL mode , so will installing the new drivers solve their problems ?
Their computers are having 256 MB ram each and Ubuntu is running slick on their comps.

THanks!!

---

### Post by glenndavy on 2007-03-17
hi ashmew - quick question (or comment?) you havent actually said what their problems are for us to try and fix...I dont remember with dapper specifically, but i think you'll find xorg is just set up with i810 driver automagically... i have an i810 and an i915 box and I dont recall having to 'get it to work'... so are they *actually *having a difficulty (and if so what is it?)  or are you just asking pre-emptively?

anyhow...here's   a 'pre-emptive' answer...

open up a terminal, then...
```

sudo dpkg-reconfigure xserver-xorg

```

and follow the bouncing coconuts... you'll be able to select the i810 driver along the way.  AFAIK its installed by default, but if not, you can verify like this

```

dpkg -l |grep -i xserver-xorg-video-i810

```

you'll probably get back something this (except it will reflect the your version, not mine):
```

ii  xserver-xorg-video-i810                      1.7.4-0ubuntu1                             X.Org X server -- Intel i8xx, i9xx d...

```

but if you get nothing, its not installed.

If thats the case
```

apt-get install xserver-xorg-video-i810

```

should prompt you to put in cd and install the driver. you may or not then have to dpkg-reconfigure as per the top of this post... but like i said, i think its all already been done for you.

---

### Post by ashmew2 on 2007-03-18
HI glenn.thanks for the info...acctually they want to run counter strike 1.6 on their systems , so is direct rendering (as counter strike needs OpenGL to run) turned on by default in dapper when using i810 ? I hope u got me question!!

---

### Post by glenndavy on 2007-03-18
hey there - I thought it was... but i just looked at two of my systems and neither are, as some point I had games going from my steam account a few mnths back... anyhow... i'll investigate as ive got time over next couple of days - see what I can learn
 
in meantime... perhaps some other helpful soul will know off top of their head and help us out ;-)

---

### Post by ashmew2 on 2007-03-27
bump

---

### Post by ComputerGeek31618 on 2008-06-18
I've noticed some problems with my onboard intel 845's 3D in Ubuntu Gusty.  3D applications will not run or 3D objects will not render correctly.  For example, with the flying toasters screensaver, you see the inside of the toaster in front of the outside... that sort of thing.  One of the tunnel screensavers shows a portion of the tunnel past the turn up ahead where you should only see the nearest wall.  I tried playing a 3D game in Wine, and it crashed, but that could be a different issue.  Is there a better driver for the 810/845 than the one included by default?  Is there something I can do about it?

Just another note, I installed Kubuntu Hardy with KDE 4, and have since not seen anything happen, but I have not seen any 3D applications either.  And is it possible that (k)ubuntu Hardy has better intel 845 drivers?

---

