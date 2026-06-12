---
title: "No X windows HELLP!!!"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-10-12
Hi everyone,

Well it was all going so well, I really am starting to get to grips with Ubuntu, anyway I changed my monitor settings using "sudo nvidia-settings", I'm using twinview and I changed it to clones so that both my monitor and tv look the same.  All seemed well and so I saved the new setting to the config file.  Anyway on re-booting my computer no longer boots up properly. It gets so far and then tells me there is a problem with X-windows or something.  It lets me see some information on this, something about /etc/X11/config (I'm going form memory here) and eventually leves me with a black screen on which I can type but nothing happens when I do.  Clearly something has gone wrong with that file, probably when I saved the new settings but how do I get to the file to edit it, or how do I revert to some basic safe setting?  I can't seem to use the computer at all so how do I fix it??

Please help
and please please tell me there is something I can do other than format and start again :confused:

---

### Post by renzokuken on 2007-10-12
boot up until the x error appears, press Ctrl+Alt+F1 to get to a tty terminal screen, log in and run

```
sudo dpkg-reconfigure xserver-xorg
```

this wizard will help you change your settings, it edits the xorg.conf for you (the file you are trying to remember from memory

/etc/X11/xorg.cong

---

### Post by tony.morse on 2007-10-12
Brilliant, thats exactly what I needed to know! Thanks, I'll post again if it works when I get home form work!!

---

### Post by tony.morse on 2007-10-14
Brilliant that worked, soz for taking so long to confirm that.

So my next question is... is there some guide or tutorial I can follow to get more familiar with this stuff?  I mean the command is pretty obscure I wouldn't have guessed dpkg ??

---

### Post by forestpixie on 2007-10-14
I'm sure that there is somewhere but never found it myself :( the [wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") can be helpful

but I found that reading threads was enormously helpful - write things down or have a text doc you can put them in

---

### Post by tony.morse on 2007-10-15
Solved

---

### Post by forestpixie on 2007-10-15
to set thread as solved can you use thread tools

---

### Post by tony.morse on 2007-10-16
nope, thread tools doesn't let me do that?

---

### Post by skymera on 2007-10-16
Gutsy automatically changes to a driver that works :)

so perhaps no more 'X has failed' sign.

but remember those commands and your safe :wink:

---

### Post by Pinger05 on 2007-10-16
Before you begin any of that I would suggest you back up /etc/X11/xorg.conf.  Easy way is to open a terminal then type in:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

That way if you get the blue screen you can boot up into safe mode via grub and copy the backup file.  Good luck!

---

