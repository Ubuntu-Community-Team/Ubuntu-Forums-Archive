---
title: "automate startx in xubuntu"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Tobitas on 2006-03-15
absolute noob question:

how do I make xfce start automatically after login in? In the instructions I used it only says: just type xserver. For automating this, put it into the init files.
Which init files? What do I type there?

Thanks.

---

### Post by henriquemaia on 2006-03-15
If you use GDM as your login manager, choose XFCE as your default session and on gdmsetup make your user login automatically. 

```
sudo gdmsetup
```

Hope this helps.

---

### Post by stuporglue on 2006-03-15
You could also add a bash script to your .bashrc

.bashrc gets run whenever you log in. You could do something like 

> XISON=`ps ux | grep xserver | wc -l`

if [ "$XISON" != "1" ]
then
   startx
fi

It just checks if the xserver is running or not, and if it's not, it launches it. Note that I wrote this at work on a Windows box, so I can't test it. If should be close to the right thing though.

---

### Post by Tobitas on 2006-03-15
[QUOTE=henriquemaia]If you use GDM as your login manager, choose XFCE as your default session and on gdmsetup make your user login automatically. [/QUOTE]

So far I have not installed any login manager, tried to keep things as simple as possible. If I install gdm, will it slow down the booting process or is it merely a graphical login screen? Is there a xfce display manager available to keep things consistent?

Thanks

---

### Post by stuporglue on 2006-03-15
> So far I have not installed any login manager, tried to keep things as simple as possible. If I install gdm, will it slow down the booting process or is it merely a graphical login screen? Is there a xfce display manager available to keep things consistent?

GDM isn't very heavy and creates no noticable slowdown at boot that I notice. I install it on PIIs when I install Xubuntu, and it works fine. There is no XFCE display manager, but there is an Xubuntu theme (at least in Dapper) for GDM.

---

### Post by henriquemaia on 2006-03-15
[QUOTE=stuporglue]You could also add a bash script to your .bashrc

.bashrc gets run whenever you log in. You could do something like 



It just checks if the xserver is running or not, and if it's not, it launches it. Note that I wrote this at work on a Windows box, so I can't test it. If should be close to the right thing though.[/QUOTE]

Your code works. Tested it. Nice tip.

---

### Post by wookieman on 2006-04-01
I've tried the code and yes it works but when I try and start a terminal I get the following error...

'X: user not authorized to run the X server, aborting.'

then a long pause and the bash prompt appears. How can I fix this ?

Cheers Wookie.

---

### Post by missmoondog on 2006-04-04
how do you make the script, save it as a what type file extension, and find the file it goes in?

thanks

---

