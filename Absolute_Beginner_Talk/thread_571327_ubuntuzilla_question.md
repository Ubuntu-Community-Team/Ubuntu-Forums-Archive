---
title: "ubuntuzilla question"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-10-09
I am trying to use ubuntuzilla to install the latest firefox and or thunderbird but it doesn't seem to finish becuase it cant' get some key file? It checks a bunch of different sites but is never able to obtain this key and just quits? Anyone know of how to fix this?

Thanks,

---

### Post by philinux on 2007-10-09
> **cjnkns said:**
> I am trying to use ubuntuzilla to install the latest firefox and or thunderbird but it doesn't seem to finish becuase it cant' get some key file? It checks a bunch of different sites but is never able to obtain this key and just quits? Anyone know of how to fix this?

Thanks,

I've installed this twice now never had a hitch. Can you try again but this time take a screenshot of where it goes wrong or post the errors etc.

---

### Post by Joeb454 on 2007-10-09
As well as what the above poster mentioned, have you made sure you've followed the steps on the ubuntuzilla website without missing a step or making a typo.

As I've learnt, the CLI assumes that you know what your doing, if you ask it to delete all the files in /home it will, it won't check first. (Which is why I ask if you made no mistakes :p)

---

### Post by nanotube on 2007-10-09
> **cjnkns said:**
> I am trying to use ubuntuzilla to install the latest firefox and or thunderbird but it doesn't seem to finish becuase it cant' get some key file? It checks a bunch of different sites but is never able to obtain this key and just quits? Anyone know of how to fix this?

Thanks,

from your description i'm guessing that it's failing to get the mozilla gpg signing key. my guess is that you are behind some kind of firewall that blocks access to the gpg keyservers (they are not port 80, afaik)...

so you could take any one of the following routes:
1. manually import the mozilla gpg key, and then run again
to manually import, try command:
```
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
```
if it's thefirewall, then this will also fail - but at least it will give you confirmation :)
2. skip gpg key verification by using option "-g"
3. unblock outgoing connections (if you control the firewall, that is), and try again

---

### Post by philinux on 2007-10-09
Firewall never came into equation for my install and thats a re-install so thats default iptables too

---

### Post by nanotube on 2007-10-09
> **philinux said:**
> Firewall never came into equation for my install and thats a re-install so thats default iptables too

yea, the default firewall is unlikely to mess with you... but there was one guy who posted on the ubuntuzilla forum, that was having problems because he was behind some fancy corporate firewall or something. that's why i pointed out the possibility. :)

and btw, thanks for helping out with ubuntuzilla support ;)

---

