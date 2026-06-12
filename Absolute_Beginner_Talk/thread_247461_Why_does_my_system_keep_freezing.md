---
title: "Why does my system keep freezing?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by dittyman1 on 2006-08-30
Hello all,

Almost without fail, when I'm surfing the internet with either Swiftfox or Firefox, my system completely freezes and I have to restart.  Is there anything I can do so I don't have to keep restarting my system?  Thanks.  
](*,)

---

### Post by kinematic on 2006-08-30
use opera,epiphany or galeon ;)

---

### Post by Metacarpal on 2006-08-30
> **dittyman1 said:**
> Hello all,

Almost without fail, when I'm surfing the internet with either Swiftfox or Firefox, my system completely freezes and I have to restart.  Is there anything I can do so I don't have to keep restarting my system?  Thanks.  
](*,)

Are you, by any chance, downloading a torrent file over a wireless connection while you surf the internet?

---

### Post by dittyman1 on 2006-08-30
> **Metacarpal said:**
> Are you, by any chance, downloading a torrent file over a wireless connection while you surf the internet?

No, I don't have any sound (I think it's a driver issue) so bittorrent makes no sense to me right now.  But I do usually have GAIM running.  And, I'm thinking that it could be from a "temperamental" cable modem, since I use charter's high-speed internet.  And it goes out.  Too much.  But I know it's not Ubuntu.  Is there a way to "Force Quit," or "End Program?"  (Ctrl-Alt-Delete)

---

### Post by dittyman1 on 2006-08-30
> **kinematic said:**
> use opera,epiphany or galeon ;)

I have opera, guess I'll have to look for epiphany and/or galeon.  I really like Firefox though.

---

### Post by Mimsy on 2006-08-30
So Firefox is not a good choice for Ubuntu-based web surfing?

/Mimsy

---

### Post by Cuppa-Chino on 2006-08-30
no would not say that at all, firefox works fine for me - sometimes hogs memory but it does that on Windo$ as well

quite a few other things tend to be more tricky - check if Fireferret is hogging mem

---

### Post by dittyman1 on 2006-08-30
> **Mimsy said:**
> So Firefox is not a good choice for Ubuntu-based web surfing?

/Mimsy

I don't know.  Like I said before, it might be problems with my cable modem service.  Firefox is one of the best browsers available IMHO, I'm just having problems and I'm new to linux.

---

### Post by DC@DR on 2006-08-30
@ dittyman1, what exaclty was the scenario when you encountered the crash? I don't think Firefox has anything considered as a crash-bug, jam or smth. It's definitely a very stable, usable browser IMHO. It must be smth else you did that caused the problem. Plz clarify it so we can take a look and try to help you with your problem :)

---

### Post by dittyman1 on 2006-08-30
I have a feeling that somehow my RAM was being used up.  Usually it froze when I had multiple tabs open.  It's just Firefox using up all my RAM.

---

### Post by CarpKing on 2006-08-30
If you open up a terminal and type "killall nameofprogram" that should force quit.  You can also add a force quit button to the panel.  The System monitor will show what is running and can kill apps; if you want to set up ctr+alt+delete to bring that up, check out asyiu's post in this thread: [http://www.ubuntuforums.org/showthread.php?t=200873#5](http://www.ubuntuforums.org/showthread.php?t=200873#5)

---

### Post by skymt on 2006-08-30
How do you have virtual memory set up? Did you create a swap partition during install?

If not, here's how to set up virtual memory without needing to repartition ($ -- enter the text into a terminal; {foobar} -- replace foobar with whatever makes sense):

$ sudo dd if=/dev/zero of=/tmp/myswap bs=1024 count={size}

* Make {size} as big as you want the new swap to be. Try 512 megabytes.

$ sudo mkswap /tmp/myswap

$ gksudo gedit /etc/fstab

* Add a line that says:
```

/tmp/myswap       none            swap    sw              0       0

```
$ sudo swapon /tmp/myswap


If you do that, you won't run out of memory. Probably.

---

