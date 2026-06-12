---
title: "Editing the XORG.Conf file"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Greglu on 2008-03-12
Hello all,
I have just installed Ubuntu + Gutsy on a Compaq R4000 with a ATI Radeon Xpress 200M.

I am trying to edit the /etc/x11/xorg.conf file to change a setting, but when I do a:

sudo gedit /etc/x11/xorg.conf the file comes up blank.

Can anyone tell me what I am doing wrong.

Cheers
Greg :confused:

---

### Post by jan quark on 2008-03-12
```
gksudo gedit /etc/X11/xorg.conf
```

capital X and gksudo
but capital X is the most important part

---

### Post by Papa-san on 2008-03-12
try this:
```
sudo gedit /etc/X11/xorg.conf
```
The 'x' needs to be upper case.

---

### Post by Greglu on 2008-03-12
wow what a quick response.

Thanks alot, that did it.

I just have to say, it is a real pleasure using this OS.

Cheers
Greg:)

---

