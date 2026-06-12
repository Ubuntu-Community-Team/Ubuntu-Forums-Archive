---
title: "OMGosh I got it running... LOL"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by buggs156 on 2007-08-30
I am a first time Linux...er... I really can't believe how easy the developers have made it for installing the OS on a external HDD let alone on any HDD at all.  I have to say this OS is very sweet.  I have the Nvidia drivers already installed and effects are awsome.  Although I wish it supported a higher resolution... 1024x768 is the only supported resolution for the OS on my monitor as its a wide screen 22 inch and the optimum is 1680x1050.  Anyway I wanted to try the KDE desktop enviroment since this version was so easy to install (Ubuntu) but that will be a project for another time.  All in all it took me 20-25 minutes to set it up and get it installed... half the time to install windows. :popcorn: :)  You will see me bounce around the forums as Vista is my 2nd OS now... LOL

Dell E520 Dim.
- Intel Core 2 Duo 6420
-2 GB DDR 2 (667mhz I think don't quote me)
-Nvidia 7300 LE 128mb 256 turbocache
-320 gig hdd Vista
-160 gig hdd Ubuntu
-DVD drive
-DVD RW... the usual

:popcorn:

---

### Post by isaacj87 on 2007-08-30
> **buggs156 said:**
> I am a first time Linux...er... I really can't believe how easy the developers have made it for installing the OS on a external HDD let alone on any HDD at all.  I have to say this OS is very sweet.  I have the Nvidia drivers already installed and effects are awsome.  Although I wish it supported a higher resolution... 1024x768 is the only supported resolution for the OS on my monitor as its a wide screen 22 inch and the optimum is 1680x1050.  Anyway I wanted to try the KDE desktop enviroment since this version was so easy to install (Ubuntu) but that will be a project for another time.  All in all it took me 20-25 minutes to set it up and get it installed... half the time to install windows. :popcorn: :)  You will see me bounce around the forums as Vista is my 2nd OS now... LOL

Dell E520 Dim.
- Intel Core 2 Duo 6420
-2 GB DDR 2 (667mhz I think don't quote me)
-Nvidia 7300 LE 128mb 256 turbocache
-320 gig hdd Vista
-160 gig hdd Ubuntu
-DVD drive
-DVD RW... the usual

:popcorn:

If you're sure you run at a 1680x1050 resolution normally, just go and edit your xorg.conf to accommodate. Then you'll be back at 1680x1050 goodness!

---

### Post by Hobo Joe on 2007-08-30
You can run at a different resolution. But with the nVidia drivers installed, you don't want to do it the normal way, you want to do it with the nVidia control panel. In the terminal, run the command:
```

sudo nvidia-settings

```
Then just change the resolution how you want, click apply, then save it to x configuration.

---

### Post by buggs156 on 2007-08-30
> **isaacj87 said:**
> If you're sure you run at a 1680x1050 resolution normally, just go and edit your xorg.conf to accommodate. Then you'll be back at 1680x1050 goodness!

Whoa whoa whoa slow down there good buddy... lol... xorg.conf???  Once again a beginner... umm is there a how to... maybe you could provide me a link at how this is done.  And yes I'm sure I run at 1680x1050 that is what my monitor tells me is default/optimum res.

Thanks for the help ahead of time.:)

---

### Post by buggs156 on 2007-08-30
> **Hobo Joe said:**
> You can run at a different resolution. But with the nVidia drivers installed, you don't want to do it the normal way, you want to do it with the nVidia control panel. In the terminal, run the command:
```

sudo nvidia-settings

```
Then just change the resolution how you want, click apply, then save it to x configuration.

Thank you very much... much appreciated ignore last post.

---

### Post by buggs156 on 2007-08-30
ahhh much better... I can see clearly now the rain(pixels) is gone.:lolflag:

---

### Post by Hobo Joe on 2007-08-30
> **buggs156 said:**
> ahhh much better... I can see clearly now the rain(pixels) is gone.:lolflag:

Gotta love those worthless, but still awesome plugins!

Paint flame is still my favorite though. :)

---

### Post by PmDematagoda on 2007-08-30
I tried changing the the resolution and refresh rates but I got a notice when I tried to save them to the xorg.conf file saying that it couldn't replace the older backup of the xorg.conf file. Does anyone know how to fix this?:confused:

---

### Post by splintercellguy on 2007-08-30
You are prefixing the dpkg-reconfigure command with sudo?

---

### Post by ubuntu27 on 2007-08-30
> **buggs156 said:**
> Whoa whoa whoa slow down there good buddy... lol... xorg.conf???  Once again a beginner... umm is there a how to... maybe you could provide me a link at how this is done.  And yes I'm sure I run at 1680x1050 that is what my monitor tells me is default/optimum res.

Thanks for the help ahead of time.:)

When they give you a command or a code. you have to type it (or just copy and paste) in the terminal or konsole.

The terminal in Ubuntu is located at 
Applications Menu/Accessories/Terminal

[Where is the Terminal?]("http://www.psychocats.net/ubuntu/terminal")


I don't have a nvidia card, so I don't know much about them. But, how about follow the tip from Hobo Joe?

> **Hobo Joe said:**
> You can run at a different resolution. But with the nVidia drivers installed, you don't want to do it the normal way, you want to do it with the nVidia control panel. In the terminal, run the command:
```

sudo nvidia-settings

```
Then just change the resolution how you want, click apply, then save it to x configuration.


Good Luck

---

### Post by Hobo Joe on 2007-08-30
> **PmDematagoda said:**
> I tried changing the the resolution and refresh rates but I got a notice when I tried to save them to the xorg.conf file saying that it couldn't replace the older backup of the xorg.conf file. Does anyone know how to fix this?:confused:

Did you prefix the command with 'sudo'? That will give you root permissions, otherwise it won't work.

> **ubuntu27 said:**
> When they give you a command or a code. you have to type it (or just copy and paste) in the terminal or konsole.

The terminal in Ubuntu is located at 
Applications Menu/Accessories/Terminal

[Where is the Terminal?]("http://www.psychocats.net/ubuntu/terminal")


I don't have a nvidia card, so I don't know much about them. But, how about follow the tip from Hobo Joe?


Good Luck

He did follow my advice. :)

---

### Post by splintercellguy on 2007-08-30
A thought, but shouldn't it be gksudo nvidia-settings? It is a GUI app after all.

---

### Post by Hobo Joe on 2007-08-30
> **splintercellguy said:**
> A thought, but shouldn't it be gksudo nvidia-settings? It is a GUI app after all.

Technically, yes, but in this case, it doesn't really matter. In fact, in MOST cases it doesn't really matter.

---

### Post by isaacj87 on 2007-08-30
> **buggs156 said:**
> Whoa whoa whoa slow down there good buddy... lol... xorg.conf???  Once again a beginner... umm is there a how to... maybe you could provide me a link at how this is done.  And yes I'm sure I run at 1680x1050 that is what my monitor tells me is default/optimum res.

Thanks for the help ahead of time.:)

Sorry! I'm not that familiar with Nvidia cards either...so you and I are in the same boat in the regard.

---

### Post by PmDematagoda on 2007-08-30
Thanks this time it worked out. Seems like the only problem was that the program didn't have enough permissions so using sudo fixed it.:)

By the way thanks Hobo Joe

---

### Post by buggs156 on 2007-08-30
> **isaacj87 said:**
> Sorry! I'm not that familiar with Nvidia cards either...so you and I are in the same boat in the regard.

I followed Hobo Joe's advice and got the resolution changed.  Thank you everyone.

---

