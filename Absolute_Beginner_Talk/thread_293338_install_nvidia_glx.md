---
title: "install nvidia glx ?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-11-05
HI all!

I just allowed some updates to go through and I was suspicious about one that was to remove nvidia glx.  This happened once before and I wasn't able to get back into ubuntu after and now it has happened again.  Why do they remove something that buggers up the systen???:confused: 

Anyhow, I have done the xserver reconfigure thing and still nothing so I was wondering what is the code to install nvidia glx from the terminal?  I can get into the single user mode or whatever it is called.

Thanks.

Russty.

---

### Post by Kateikyoushi on 2006-11-05
It the grub menu select single user mode, this should boot you to terminal.
Then install nvidia-glx.

```
sudo aptitude install nvidia-glx
```

---

### Post by livinginx on 2006-11-05
One thing I always do after I make a change in xorg.conf is to save it as xorg.conf.bk and another as xorg.conf.plain

That way, I can always have something to rely on with out the whole:
```
sudo dpkg-reconfigure xserver-xorg
```

I just do
```
sudo mv /././xorg.conf.bk /etc/X11/xorg.conf
```
or
```
sudo mv /././xorg.conf.plain /etc/X11/xorg.conf
```

replace /././ with wherever you store it.

---

### Post by Russty of Oz on 2006-11-05
> **Kateikyoushi said:**
> It the grub menu select single user mode, this should boot you to terminal.
Then install nvidia-glx.

```
sudo aptitude install nvidia-glx
```

Thanks Kateikyoushi!

That did it! :) 

Russty

---

### Post by Russty of Oz on 2006-11-05
> **livinginx said:**
> One thing I always do after I make a change in xorg.conf is to save it as xorg.conf.bk and another as xorg.conf.plain

That way, I can always have something to rely on with out the whole:
```
sudo dpkg-reconfigure xserver-xorg
```

I just do
```
sudo mv /././xorg.conf.bk /etc/X11/xorg.conf
```
or
```
sudo mv /././xorg.conf.plain /etc/X11/xorg.conf
```

replace /././ with wherever you store it.

Thanks, I will keep that in mind.

Russty

---

### Post by livinginx on 2006-11-05
> **Kateikyoushi said:**
> It the grub menu select single user mode, this should boot you to terminal.
Then install nvidia-glx.

```
sudo aptitude install nvidia-glx
```

What is the difference between aptitude and apt-get and such?

---

### Post by DanSchnell on 2006-11-05
> **livinginx said:**
> What is the difference between aptitude and apt-get and such?

Now that I think about it, I want to know too...

---

### Post by Kateikyoushi on 2006-11-05
Aptitude is a front end to apt with few extra features, better to use it instead of apt.

Read more here. [LINK]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by JayTee on 2006-11-05
this post explains the difference pretty clear.
[http://www.ubuntuforums.org/showpost.php?p=1708030&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1708030&postcount=2)

---

