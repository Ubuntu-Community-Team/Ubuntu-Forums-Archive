---
title: "How to un-install Skype?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-08-16
Hi,

I have skype running, but I can only use it once before I get an error due to  an issue with GNOME's Enlightened Sound Daemon (ESD).

There is a fix of installing the Debian version of Skype - but how do I remove the old version of skype first?

Thanks,

Adeam.

---

### Post by Kobalt on 2006-08-16
Two ways : launch Synaptic, search it and select "remove completely". Or through command line : 
```
sudo aptitude remove skype
```

Cheers ! :rolleyes:

---

### Post by melissawm on 2006-08-16
Have you installed it via apt-get? If so, just do

```
sudo apt-get remove skype
```

and it should be uninstalled. If you have downloaded and installed it from the site, that is, the debian package, you should do

```
sudo dpkg -r skype
```

Hope it helps.

---

### Post by 3rdalbum on 2006-08-16
Apt-get remove, and removing through Synaptic, will still work even if you downloaded Skype from the website.

---

### Post by adam s on 2006-08-16
Thanks guys,

I installed this through the command line - and therefore did not think of using synaptic to un-install.

Now to re-install it with the debian package.

Adam.

---

