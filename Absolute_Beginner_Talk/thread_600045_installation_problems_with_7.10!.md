---
title: "installation problems with 7.10!"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by littleasian on 2007-11-01
hey guys.

i just installed ubuntu 7.10 on my computer.  while running the live-cd, everything worked good (screen resolution original size of 1280x800, etc.), but after i installed it, some components stopped working!

1.  the screen resoltion is now 800x680, and i dont know how to change it back.  i went under resolution settings and under the pull down tab, only 800x680 is listed (along with 600 x 460 i think).  how do i get my native resolution baack?

2.  i can't enable desktop effects.  I checked under restricted drivers, and the nvidia one was checked.  It was installed when i wanted to play around with compiz-fusion during the live-cd, and i guess it carried over!

3.  i noticed that i have no sound!  this occured during the live cd too...no movies, or mp3's work at all!

My computer's specs are:
hp dv6500t 
intel core 2 duo t7300 @ 2.0 ghz
nvidia geforce 8400M GS
200 gb hd (of which 15 gb is ubuntu)

Can someone help me get these things figured out??  ahhhhhh i was so excited for it to install but now alas im back on my vista install typing this msg.  On a good note, at least my wireless card works!

Thanks!!!!

---

### Post by Factory on 2007-11-01
> Can someone help me get these things figured out?? ahhhhhh i was so excited for it to install but now alas im back on my vista install typing this msg. On a good note, at least my wireless card works!

Hah, this is a good note, indeed! Many a good man/woman have gone bald pulling out their hair over wireless issues.

The resolution problem is a relatively easy fix. First a little bit about configuration in Ubuntu/Linux environments in general: Most everything (if not everything?) is done in text. That means all config files are easily edited.

The file you want to edit is under the directory /etc/X11/ and is called "xorg.conf". If you have a nasty videocard, you'll get to remember this filename/location well. You're going to want to edit you xorg.conf file by typing (in a terminal)
```

sudo nano /etc/X11/xorg.conf

```
where 'sudo' gives you super user privileges for the current command, and 'nano' uses the text editor named nano to edit the xorg.conf file. Next you'll want to look for Subsection "Display" which will be towards the bottom of the file. Look for the specific Display type that you are using given by "Depth" (most likely you're using the one labeled 24). Now, next to 'modes', just add the resolution of your monitor. close and save the file (ctrl + s and then ctrl + x), and then restart X (ctrl + alt + backspace). If the changes aren't already applied, you should be able to choose the resolution you just typed in as you would any other resolution.

As for the other problems I'm at a loss. All I can say is that google is a good friend of mine, and that Ubuntu users may not be the only ones having the same problem with the same hardware specs as you.

---

