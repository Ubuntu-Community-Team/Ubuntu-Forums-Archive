---
title: "No screen."
date: 2007-06-29
forum: Apple Intel Users
---

### Post by makaira on 2007-06-29
I followed the guide @ [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro) and have run into some problems. I'm installing with Feisty Fawn Alt disk and after everything was said and done I was left with an error. It went something to the tune of, "Screens found but none have a usable configuration" and "fatal server error: no screens found."

Now I'm somewhat confused as what to do next.

Edit: I may try some tricks from [http://ubuntuforums.org/showthread.php?t=413713](http://ubuntuforums.org/showthread.php?t=413713)

---

### Post by luisbg on 2007-06-29
post here your /etc/X11/xorg.conf to see if we can spot any errors. the problem must be there.

luis

---

### Post by luisbg on 2007-06-29
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

that thread can be very useful for you... founded in 
[http://ubuntuforums.org/showthread.php?t=485477](http://ubuntuforums.org/showthread.php?t=485477) <- who had the same problem as you

---

### Post by makaira on 2007-06-29
Thanks. I actually was able to get it to work while you were posting that. I'm now posting from ubuntu! Now I have an entirely different set of problems:

(1) Wireless Network - I'm on a university campus and the wireless has a username and password, and the wireless software that comes with ubuntu doesn't seem to have a username option. Any ideas?

...and a problem infinitely worse...

(2) For some reason, as I type anything, and as I'm typing this, text is randomly inserted everywhere and anywhere, and sometimes new webpages open. It's seems as if the keyboard has intense ADD and will do barely anything I tell it to. Writing these few sentences has taken longer than it would normally take me to write a few pages...

---

### Post by makaira on 2007-06-30
As for the wireless network, I tried to install MadWifi. I first got the build with HAL, then noticed some errors in relation to HAL so I tried to install the version without HAL and now it's giving me a "permission denied" on removing the old files. Also, it's not letting me to change to root. It just says:

```

su: Authentication failure
Sorry

```

---

### Post by Siljrath on 2007-10-20
> **makaira said:**
> As for the wireless network, I tried to install MadWifi. I first got the build with HAL, then noticed some errors in relation to HAL so I tried to install the version without HAL and now it's giving me a "permission denied" on removing the old files. Also, it's not letting me to change to root. It just says:

```

su: Authentication failure
Sorry

```

i too have been getting seemingly illegitimate authentication failures.
and made a thread about it here: [http://ubuntuforums.org/showthread.php?t=584127](http://ubuntuforums.org/showthread.php?t=584127)

i had been trying to install virtualbox, but hadnt done anything to the system that would cause this (as far as i can tell, 'cos i've done bugger-all).


whats the story with this quirk?


has ubuntu got too much "character" and is acting independently like i was sure my old win98 did?

:lolflag:

---

