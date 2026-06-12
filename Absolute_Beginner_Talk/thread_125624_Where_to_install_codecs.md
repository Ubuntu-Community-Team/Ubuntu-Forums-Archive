---
title: "Where to install codecs??"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by bartbes on 2006-02-04
I have downloaded the w32 codecs but I don't know where to install / put them. And do all programs have a different codec dir? (if yes I want to install the codecs for mplayer and maybe totem)

---

### Post by aysiu on 2006-02-04
If you downloaded the w32codecs as a .deb file to your desktop, go to Applications > Accessories > Terminal and type ```
cd Desktop
sudo dpkg -i w32*.deb
``` The password is your password (assuming you were the first user created during installation).

---

### Post by bartbes on 2006-02-04
I downloaded them as a tar.gz

---

### Post by Klaidas on 2006-02-04
According to the wiki page:
> If your country's laws allow you to play media using the w32codecs, use your web browser to download the file w32codecs_20050412-0.0_i386.deb from [WWW] here or [WWW] here **to your Desktop**, and, in a terminal, type:

```
cd ~/Desktop
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```


However, you can install them easier, like using [Automatix]("http://www.ubuntuforums.org/showthread.php?t=114251")

EDIT: aww, didn't make it in time

---

### Post by aysiu on 2006-02-04
[QUOTE=bartbes]I downloaded them as a tar.gz[/QUOTE] That only makes things more complicated. You can get the .deb right [here](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb).

---

### Post by kewl1uk on 2006-02-04
I followed the instructions on the Restricted Formats Wiki page at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

By clicking the lifesaver icon on your desktop you can go to Ubuntu 5.10 Starter Guide > Applications > Music and Movies. What in there that's missing from the Wiki is:
```
gst-register-0.8
```

I don't know whether it's actually necessary to do that if following instructions in the Wiki but I did it and all is well. The only multi-media files I can't play are the .mov movie trailers on apple.com but I can play .mov files from elsewhere.

---

### Post by bartbes on 2006-02-05
aysiu, thx for the link.
downloaded and installed them (much easier with kubuntu-dekstop I must say) everything is now working fine

---

