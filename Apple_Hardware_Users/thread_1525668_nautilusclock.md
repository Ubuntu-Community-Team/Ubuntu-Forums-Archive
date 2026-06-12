---
title: "nautilus/clock"
date: 2010-07-07
forum: Apple Hardware Users
---

### Post by dzon65 on 2010-07-07
A while back I installed Debian on an imac G3.Since it's for someone who will be using linux for the first time,I decided to have a "easy" interface installed.So,I went for a ubuntu look.Changed the the wm to openbox and fm to thunar however to speed up things.Everything worked just fine until yesterday.When booting,it came up with an error-window that nautilus wouldn't run as it's suposed to.The keyboard layout changed randomly as well.Finding out more about it didn't work (in that same window).Cpu was skyhigh and indeed huge parts of the menu were missing.Avahi daemon took the biggest part of it,so I deleted it.Cpu was still maxed out (now xorg taking the biggest) but then I got the message that the internal clock wasn't set wright.(It was before however).I hope there's a way to set the internal clock and getting things back as they're suposed to be without having to do a complete reinstall.The xorg.conf file needed to get this thing running was a)quite big, b)hard to type since the first letters were hidden offscreen.
If I DO have to do a reinstall,isn't there a way of inserting the xorg.conf file using the http where I found it?

---

### Post by linuxopjemac on 2010-07-07
It looks like your PRAM battery died.
[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0)

---

### Post by dzon65 on 2010-07-07
Quote:To do this access open firmware by booting the computer while holding down the O, F, Apple and Option keys. The command to set the date and time is:

What are the keys with a non-apple keyboard?

---

### Post by dzon65 on 2010-07-07
Linuxopjemac.
Looks like I'm heading for a reinstall (keyboard's changed from azerty to qwerty to qwertzu to....what's next).
Doesn't matter to what I set it,keeps changing.So will be a bit difficult to set the clock.:cry:
Is there a way to install that xorg.conf without having to type it allover again?

---

### Post by linuxopjemac on 2010-07-07
Just post it here and I will serve it for you. You can wget it from the terminal after installation. Just like you downloaded the Mintinstaller script.

---

### Post by dzon65 on 2010-07-07
I have the link to it,but I don't really now how to do it.And,if the pram battery's a near goner,it probably would have to be replaced in order not to have the same issues in the future.But those folks don't really wanna spend a penny on it.
Still,would've been intresting to learn how to wget a xorg file.I'm a computer neanderthal you know.

---

### Post by linuxopjemac on 2010-07-07
What you have to do is install ntp. The date and time are set during boot and then you won't have trouble with logging in and stuff like that.

```
sudo apt-get install ntp
```

---

### Post by dzon65 on 2010-07-07
Thanks.Gonna get that battery myself.It would be really stupid to ditch this mac cause,what 10 euros max for the battery,is a too huge cost (!?!?).Don't get certain people.

---

