---
title: "[SOLVED] Gibberish log-in screen"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by cf1709 on 2007-10-31
I just installed Gutsy alongside Windows XP

The startup loading screen looks normal:

[IMG]http://i148.photobucket.com/albums/s9/cf1709/Image011.jpg[/IMG]

But the login screen looks like this:

[IMG]http://i148.photobucket.com/albums/s9/cf1709/Image013.jpg[/IMG]

I took it with my camera phone so the quality is a bit off.

I've been reading for sometime now that "Via/S3G Unichrome IGP Pro" (my video adaptor) isn't that good with 3D but the login screen shouldn't be like this right? I was able to install with the Live CD without any visual problems. BTW, my monitor is EMachine eView 17s. At that time (the second screen shot), the resolution is at 1280 by 1024.

Uhh... Please answer in poor man's terms. Help will be greatly appreciated. Good day.

---

### Post by tubasoldier on 2007-10-31
it is more than likely because Gusty has XGL installed by default. Don't ask me why I think its rediculous. But it is more than likely for ATI cards that can't use AIGLX.

boot into rescue mode and type in:
```
sudo apt-get purge xserver-xgl
```

That should take care of it. I think

You will also have to put in your admin password when it boots. You will have no graphics just command line.

after that is finished just type "reboot" and it should restart your computer.

---

### Post by cf1709 on 2007-10-31
I just did the thing you posted. The response is:

> Package xserver-xgl is not installed, so not removed.

---

### Post by tubasoldier on 2007-10-31
Not to second guess you, but did you spell it right? Just wondering because you misspelled it on your reply.

Anyways, sorry that didn't work for you. I'm at a loss. xserver-xgl was installed on mine by default. 

Anyone else who could help here?

---

### Post by cf1709 on 2007-10-31
I'm sure I typed it right. Thanks for your reply but it seems that that thing did not cut it. I hope somebody helps out soon...

---

### Post by uclalinux on 2007-10-31
from grub boot into the rescue mode, then type in this to your terminal  
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

This will redo your Xorg.conf file, so maybe you can get gnome running.

---

### Post by cf1709 on 2007-10-31
I don't know how but reinstallation of Gutsy did the trick. Thanks for the help guys!

---

