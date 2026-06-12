---
title: "help needed please"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by africanimport on 2005-10-31
Hey, 

I have just finished installing Ubuntu on I must admit a pretty ancient laptop, around 600mhz, 128mb ram, intel pentium 2. The installtion went fine however Ubuntu won't load. It says its loading ubuntu and asks for my usernam and pass and then says I have one new mail message about warranty and then does absolutely nothing, not even load the desktop or anything. Could I get some help, it would be really appreciated. Cheers

---

### Post by doc_holiday on 2005-10-31
type "startx"

---

### Post by africanimport on 2005-10-31
I have aleady tried that. It then says I am not authorized to start up sever X or something like that, I then tells me it doesnt understand my command.

---

### Post by ubuntu_demon on 2005-10-31
try this :

$sudo dpkg-reconfigure xserver-xorg

During the configuration program just press enter if you don't understand something and choose the simple monitor configuration. it automatically creates a backup of your xserver configuration file ( /etc/X11/xorg.conf )

After this type :
```

$ sudo init 1

(wait for a bit)

$ sudo init 2

```

Or do a restart.

I hope this helps. Otherwise we have to look somewhat deeper into your problem :).

---

### Post by africanimport on 2005-10-31
Thanks a lot, I will try this shortly, there may have been an error somewhere in the installation it was slightly slow, if that doesn't work I shall re-install Ubuntu

---

### Post by ubuntu_demon on 2005-10-31
reinstalling probably won't make a big difference. But it can't hurt to try.

If my former "solution" doesn't solve anything -->

What kind of videocard do you have ?
What's the result of :
$ lspci

post your /etc/X11/xorg.conf
post your /var/log/Xorg.0.log

also try this :
$sudo apt-get install ubuntu-base ubuntu-desktop

and look if anything gets installed.

I don't want to scare you so let's first do these things :).

---

