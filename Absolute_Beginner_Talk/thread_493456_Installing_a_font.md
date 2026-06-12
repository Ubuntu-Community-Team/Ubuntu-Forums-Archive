---
title: "Installing a font"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-07-05
Hello all,

I really wanted to install the Tahoma font so I can see Steam...so I found a website and downloaded the font. The .zip gave me 2 files

tahoma.ttf 
tahomabd.ttf

I had already installed msttcorefonts so I figured I would drop these two files into its folder:

I went to terminal, did a "sudo nautilus" and copied the two files into /usr/share/fonts/truetype/msttcorefonts

So far everything is working perfectly...so I have 2 question:

1) Can I repeat the same process for other new fonts I want to install? 

2) Am I screwing anything up by doing it this way...is there some specific (or easier) method to installing a new font?

Thank you!

EDIT: BTW if anyone wants the Tahoma font, I'll gladly upload it here.

---

### Post by testube_babies on 2007-07-05
I've made the folder /usr/share/fonts/myfonts and put all of my custom fonts in there.  It seems to work well, I've been doing it for years and have seen no side effects.

To install new fonts, I just move them to that folder and then "sudo fc-cache -f"

---

### Post by isaacj87 on 2007-07-05
I don't know if it's like this for everyone who installed msttcorefonts, but it effects Firefox. I noticed that now the Ubuntu Forums show up in tahoma after installing tahoma into the msttcorefonts folder (i think). Would creating a new custom folder for fonts not effect applications like Firefox?

---

### Post by testube_babies on 2007-07-05
No, Firefox will use Tahoma so long as it is in the font cache and that's what the website calls for.  

I think Tahoma looks like crap on Linux, and it's used on a whole bunch of websites, so its the first font I uninstall :).  But if you need it for Steam, then I think your out of luck.  Maybe there are some hidden options in about:config?

---

### Post by isaacj87 on 2007-07-06
I'll have to check that out and see.

Thanks for your help!

---

### Post by avik on 2007-07-06
I usually put the fonts straight in /usr/share/fonts/.  Really, it doesn't matter as long as you put them in that directory or any of its subdirectories.

Just make sure to run:

```
sudo fc-cache -f
```

---

### Post by forrestcupp on 2007-07-06
Actually there is a hidden font directory in your /home directory.  Just enable the showing of hidden files in nautilus and you will see a folder called /.font  The dot before font means it is a hidden folder.  You could have just put your font files in that folder without needing super user privileges and it would have worked the same.  If there isn't a folder named /.font, you can make one and it should work.

---

### Post by avik on 2007-07-06
> **forrestcupp said:**
> Actually there is a hidden font directory in your /home directory.  Just enable the showing of hidden files in nautilus and you will see a folder called /.font  The dot before font means it is a hidden folder.  You could have just put your font files in that folder without needing super user privileges and it would have worked the same.  If there isn't a folder named /.font, you can make one and it should work.

Yeah, but I like having all my fonts in one place, instead of on a user by user basis.  Just a personal preference thing.

---

### Post by forrestcupp on 2007-07-07
> **avik said:**
> Yeah, but I like having all my fonts in one place, instead of on a user by user basis.  Just a personal preference thing.

Well, that's a good point.  I've never ran more than one user on my computer.

Also, I don't know what I was thinking anyway.  I said that the folder is called /.font but it's actually called /.fonts

---

### Post by dptxp on 2007-07-07
Kubuntu has add fonts in system>. Since I have added kde-core, I just log with KDE and install fonts.
Just another way.

---

