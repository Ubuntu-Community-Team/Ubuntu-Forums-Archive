---
title: "macbook gutsy (7.10) xorg and syanptics problem (xorg.conf, where?)"
date: 2007-09-16
forum: Apple Intel Users
---

### Post by qzio on 2007-09-16
Hi!
I'm using a macbook rev1 and are currently using the gutsy repos. I have a custom compiled kernel to be able to use sleep-thingy. Problem here is that nothing happens when i close the lid, i have to click the battery-symbol and then suspend to get the computer to sleep, then i can close the lid. It wakes up when i raise the lid. I can live with this but ain't completly satisfied...

anyways, as the title suggest, my xorg is kinda broken, Yesterday i did a apt-get upgrade and it seemed to install new xorg-packages, i've read about the new 7.3 and the displayconfig-gtk thingy and it's all good i thought...

I dont know whats wrong but the performance in X is lousy. It's like a 3/86 or something, sure i have compiz enabled, the cube works, but it LAGGS. Moving windows around is not pretty, and scrolling in firefox is _slow_
Ok, lets fix this with the xorg.conf i thought! ... hmm.. nah. xorg.conf isn't used since im writing this from x without an existing xorg.conf in my /etc/X11 dir, or any other dir for that mather...

Ok, so I take a look at the displayconfig-gtk thingy. Nice! intel-graphic is in the list!...*restart*  same problem, the performance is below acceptable. (unable to watch movies at a good framerate etc)

I've also realised that my synaptic settings isn't working. Ive installed gsynaptics but they tell me to add the shmconfig true option in my xorg.conf... Yeah, since i dont have a xorg.conf file this is hard :)

So basic questions:

* Is the displayconfig-gtk thingy getting its own button in the system->admin menu? (I, my self was forced to go looking with google to find out the name and then start it from a terminal) I've read that there should be a 'advanced' button in the resolution window but i do not have such a button 

* is there an easy way to get my performance back as it was before the upgrade? i'm stuck, all i can think of is that the driver is at fault.. (im using the intel 945 one... lspci tells me intel 945)

* where is the xorg.conf configuration moved? can i edit that file? or am i forced to use the gui?(which btw, isn't complete, alot of the settings are missing)

Im really happy about gutsy and ubuntu in general, i'm aware that gutsy is "in development" so all I can blame is my self. But still i want to press hard that the macbooks are common laptop that should be supported _good_ with everything working with as little configuration as possible (i'm ok with installing extra packages and so on)

---

### Post by w4ett on 2007-09-17
As far as I know, xorg.conf is still in the same old place....

> /etc/X11/xorg.conf

I don't believe we will be getting Xorg 7.3 in Gutsy....still a bit buggy as I was told, but the GUI config we are getting...(haven't done my daily update yet tho.... :) )

Which driver are you using? the  current xorg-driver-intel?

Final comment:  Gutsy is turning out pretty nice..I've had no problems since I installed about a month ago//no crashes or issues at all...if it's this good now, the final should be stellar.....

---

### Post by cyberdork33 on 2007-09-17
Make sure to use "intel" driver in your xorg.conf

Gutsy will have Xorg 7.3, but not including xserver 1.4 (still at 1.3)

---

### Post by j4play on 2007-09-17
yeah i can't find my xorg.conf either.
not in /etc/X11
there is a copy in /usr/share/xresprobe/  but not sure if its referenced from there.

---

### Post by jokerejoker on 2007-09-19
As I understand on the X.org server 7.3 there is no xorg.conf file, it's build to auto detect all options for display driver...

---

### Post by w4ett on 2007-09-19
> **cyberdork33 said:**
> Make sure to use "intel" driver in your xorg.conf

Gutsy will have Xorg 7.3, but not including xserver 1.4 (still at 1.3)

I'm using Gutsy now, and at the moment it uses 7.2  My xorg.conf is where it always was  /etc/X11/xorg.conf......I have heard it discussed that 7.3 won't be included til Hoary.

---

### Post by cyberdork33 on 2007-09-19
> **w4ett said:**
> I'm using Gutsy now, and at the moment it uses 7.2  My xorg.conf is where it always was  /etc/X11/xorg.conf......I have heard it discussed that 7.3 won't be included til Hoary.
Yes, you are correct, but they are upgrading the modules (Xorg 7.3 stuff) in Gutsy to be used in conjunction with xserver 1.3. At least this is my understanding unless something has changed.

[http://www.desktoplinux.com/news/NS4979518777.html](http://www.desktoplinux.com/news/NS4979518777.html)

So, you will still require an xorg.conf file...

---

### Post by cyberdork33 on 2007-09-21
> **qzio said:**
> * where is the xorg.conf configuration moved? can i edit that file? or am i forced to use the gui?(which btw, isn't complete, alot of the settings are missing)
run this, it should regenerate an xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

