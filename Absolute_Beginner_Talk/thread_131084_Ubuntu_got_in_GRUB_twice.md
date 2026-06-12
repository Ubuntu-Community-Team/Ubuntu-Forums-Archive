---
title: "Ubuntu got in GRUB twice"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by darkbullet87 on 2006-02-15
When I boot up the computer, it boots into GRUB (obviously). GRUB lists my installed OS's as follows:

Ubuntu Linux Kernal 2.6
Ubuntu LInux Kernal 2.6 (Safe Mode)
Ubuntu Linux Kernal 2.6
Ubuntu LInux Kernal 2.6 (Safe Mode)
Windows XP 

As you can see, Ubuntu is listed twice. At first I thought perhaps I installed it twice (on two seperate partitions) but when I booted into the second one, it's identical to the first...as in, it's the same insalation of Ubuntu. How can I get that second listing of Ubuntu off of GRUB without reinstalling everything?

If there isn't a way, thats fine too..it's just annoying to have 2 entries of the same thing in there. :)

---

### Post by manicka on 2006-02-15
Most likely you have two kernels installed

---

### Post by darkbullet87 on 2006-02-15
[QUOTE=manicka]Most likely you have two kernels installed[/QUOTE]

Ok, so how woud I go about uninstallling one of them...and if I uninstall one, will it effect the other?

---

### Post by nurdin on 2006-02-15
The way that I normally check for extra kernels (and remove older ones) is through synaptic, search for packages linux-image. There is a green square beside all the ones installed, select any kernel older than the newest one (that you want to get rid of) and right-click choosing mark for complete removal. Then click apply button.

If you just want to get rid of the second two references do the following:

Edit your /boot/grub/menu.lst file and remove the second (two) references to ubuntu. That should do it. I don't remember if you have to do anything special after that but I don't believe you do.

---

### Post by gord on 2006-02-15
you could also edit the file /boot/grub/menu.lst but be warned, make a backup first and make sure you know what your doing :)

---

### Post by darkbullet87 on 2006-02-15
haha...yes, I've learned after many years of working with windooz, to ALWAYS make a backup LOL.

Thanks for the help!...I have to run to class right now, but I will definetly take a look at the /boot/grub/menu.lst when I  get back, and post back here how it turns out. 

Thanks again!

---

### Post by darkbullet87 on 2006-02-15
Wow....I edited out the menue.list like you said, and it's working perfect how

thanks :)

---

