---
title: "Help! I've broken it!!!!!"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-05
I have an Acer TravelMate 4101 with a wide screen and was sick of the aspect ratio being wrong in 1024 X 768 and wanted to change it to 1280 X 800, so that things don't lokk stretched and circles are round.

Foolishly, I used:

sudo dpkge-reconfigure xserver-xorg

When I re-booted things were awfully wrong and it asked me if I wanted to examine the xorg.conf file.
Unfortunately, whatever I did was terminal, as I tried to answer Yes (Y) but the system was frozen and ignored the keyboard.

I tried booting-up in recovery mode, but this didn't work either.

I have attached the two xorg.conf files (before and after) and hope that someone can lead me through on how to recover, wiyhout doing a full re-load.

Regards,
Roger. :-k

---

### Post by ramjet_1953 on 2006-09-05
Sorry, I forgot to attach the two files, that I extracted using Windows.

Roger

---

### Post by key on 2006-09-05
Did you try just copying the old xorg.conf file back to /etc/X11/. ? 

It may not get you to 1200x800, but it should get you a working X-server  again. 

I think your problem is here:

---- your new file (xorg.conf)
< Section "InputDevice"
<       Option          "UseFBDev"              "true"

---- this is missing from your old file (xorg.conf.20060905114424.txt)

This probably doesn't hurt much , but delete it. 


---- your new file (xorg.conf)
<       HorizSync       56-60

---- your old file (xorg.conf.20060905114424.txt)
>       HorizSync       28-64

If your Horizontal sync is wrong, all kinds of crazy things can happen. Try setting this back to the orignal values of '28-64'. What does Acer recommend?

Look in /var/log/Xorg.0.log to see what error messages the X server is giving you when you start it.

---

### Post by wjp.reg on 2006-09-05
Had a look at your xorg.conf file and looks like you're running an intel GPA.

You need to re-run

```
dpkg-reconfigure xserver-xorg
```

and set everything back to the way it was before the trouble.

Then apt-get 915resolution or using synpatic, install this resolution modify tool for intel graphic chip sets.

You should be ok then ;)

---

### Post by ramjet_1953 on 2006-09-05
Hi, Guys!
Thanks for the info, but how do I do this?
I said in my previous post that everything freezes.
I am a "command line newbie" so I have no idea how to do what you are saying.
Linux 101 please!

Regards,
Roger

---

### Post by key on 2006-09-05
I think your video is freezing because possibly your Horizontal sync rate is wrong. Whenever the X-server starts, it reads the xorg.conf file, tries to load a possibly unsupported framebuffer device (FBDev) and then sets the wrong sync rate for the video, and the video locks up. I think. 

If I am right, then you'll need to do some command line stuff. When everything is frozen, can you get to a terminal by pressing **ctrl+alt+F1** ? 

Hopefully this is possible, it will make things easy. If, when it is frozen you can get a terminal by the above keystroke, then log in at the prompt and 
"**sudo cp (wherever it is)/xorg.conf.20060905114424.txt /etc/X11/xorg.conf**" 

so, if xorg.conf.20060905114424.txt is in /etc/X11/ then just type:
"**sudo cp /etc/X11/xorg.conf.20060905114424.txt /etc/X11/xorg.conf**" .

You can save the old xorg.conf if you want, but it is broken and you already posted it here so you can get it back if you need it. 

If you cannot get a prompt via **ctrl + alt + F1**, we'll have to try something else. 

BTW- sorry for the slow response - having some serious forum speed issues for some reason

---

### Post by key on 2006-09-05
Oops - one more thing I left out - (sorry!!)

After you copy the file,
type "**sudo reboot**"  to reboot the machine.
 
There are other ways without rebooting, but this is probably the easiest.

---

### Post by ramjet_1953 on 2006-09-05
No joy!

When I boot up normally, it freezes and doesn't respond to cntl+alt+f1.
When I boot up in recovery mode, I appear to have a terminal, but again, no response to the keyboard.

Where do I go from here?
Is there a program that will allow me to modify the xorg.conf files from Windows? 
I can look at them and export them, using explore2fs, but because I don't have write permissions, I can't rename the old file and delete the new.

Regards,
Roger :(

---

### Post by key on 2006-09-05
Strange that the keyboard doesn't work, even in recovery mode. I don't know why that would happen, but I don't think it has anything to do with the X-server. Maybe your dpkg-reconfigure job messed up more than xorg.conf.

The only way to edit files on the ext3 partition from windows, that I know of, is to use a windowsXP ext2/3 system driver. I have never used one ( I don't have a windows partition) but this one advertises read/write support.

[http://www.sourceforge.net/projects/ext2fsd](http://www.sourceforge.net/projects/ext2fsd) 

Hopefully the install is relatively painless. Then you'll be able to write to your linux partition from windows. 

Another way that you could edit the file though, and this might be a lot easier and is what I would do, is to boot from your ubuntu CD. You should be able to find your disk and edit the xorg.conf file without much problem- and in the comfort of a functional Xserver. That's if your acer laptop plays nice with the live CD.

---

### Post by ramjet_1953 on 2006-09-05
Thanks for the tips!
I'll give it a try and get back to you.

Regards,
Roger :)

---

### Post by ramjet_1953 on 2006-09-05
All fixed!!!!
I tried the Ubuntu disk, as you suggested, but to no avail, as I am unfamiliar with the Unix syntax.

I then went into Windows XP, dowloaded the ext2fsd software, loaded it, configured it for my Linux partition and the rest was sweet, as I just used Total Commander to rename the broken xorg.conf file to a bak extension and then restored the old.
Piece of cake, and all done with a graphical environment.

As much as I like the concept of Linux, the Linux gurus need to understand that the vast majority of users are just that, "Users".
They are not interested in becoming "Geeks", and they especially don't want command lines to do things.
Linux will never become mainstram, unless it is made much easier for those of us wheo just want to get on and do our work using a computer as a tool, not a toy.

Anyhow, enough of my 2 cent's worth.

Thank you again for the prompt and accurate assistance.

Regards,
Roger:D

---

### Post by key on 2006-09-05
Roger,
Glad to hear things worked out. 

I agree with your assessment of the command line. It is a steep learning curve and is not for everyone. 

That said, **linux on laptops is not quite ready for prime time**- in my opinion. Unless you want to get a bit geeky. ;) Maybe ubuntu should mention that to first time linux users who intend to install on their laptops. On the desktop, however, things go really smoothly most of the time. 

I know there is a world of difference between the dapper install on my dell inspiron laptop and the breezy install on my desktop.

It's cool that the windows ext2/3 drivers worked for you. Next time I have a windows partition, I'll check that out. 

all the best-
key

---

