---
title: "login interface?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by zyx on 2007-03-13
Hi, there,

I set the kde, gnome and Xfce, however, my login interface has only Debian GNU/Linux interface, I can not do any choice. When I login the kubunto 6.06, it has only Xfce, but I type startkde, it works fine! my problem is how do I set up some things, I can choose KDE, Gnome or Xfce faces! Thanks?

---

### Post by Bachstelze on 2007-03-13
I'm afraid I don't understand your question very well. Do you mean that in your login screen, you can only start XFCE and not KDE or Gnome ? Aren't they in the Sessions menu ?

---

### Post by buuntuu! on 2007-03-13
hi zyx, 
there should be a "select session" button on the bottom left side of your login screen...
no idea if i understood your question exyctly, though...

---

### Post by zyx on 2007-03-13
Yes, I mean in my login screen, you can only start XFCE and not KDE or Gnome ?
I do not have session menu! I think I miss some thing to set up! but I do not know what I do miss! so this is the problems! Does any one give me some clue? Thanks!

---

### Post by buuntuu! on 2007-03-13
what exactly did you install? ubuntu, kubuntu or xubuntu?
how did you install the other two window managers?

---

### Post by zyx on 2007-03-13
I set kubuntu 6.06! I use adept to set gnome and kde and remove some programs! I think remove some programs are wrong! Now in my login screen, I do not have menu! just Debian GNU/Linux login screen, when I login it, it is Xfce, I type startkde in terminal, kde starts!
Now my problem is how to add menu in my login screen??? Thanks!

---

### Post by buuntuu! on 2007-03-13
hm, try reinstalling kde
```

sudo aptitude update

sudo aptitude install kubuntu-desktop
```

further descriptions [here]("http://www.psychocats.net/ubuntu/")
but if you messed around and can't get it right anymore consider reinstalling, might save you some time...

---

### Post by zyx on 2007-03-13
Thank you very much for your reply!
however, when I run   "sudo apt-get install xubuntu-desktop" I got the error as follows:

Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems

How do I fix this? Thanks!

---

### Post by buuntuu! on 2007-03-13
well, as it says:
```
apt-get update
``` ;)
however, the automatix error message should not be related to your problem

try aptitude instead of apt-get if it doesn't work out

---

### Post by zyx on 2007-03-13
apt-get update does not fix the PUBKEY problem!!! Any other suggests? Thanks!

---

### Post by Rui Pais on 2007-03-13
that messages is harmless (note that some times automatix is harmful, use it but don't complain much about it if you found your self in trouble)

check [here]("http://www.getautomatix.com/wiki/index.php?title=Installation") how to solve the message issue (do: 1st step till 4th step).

---

### Post by PurplePenguin on 2007-03-13
That problem is related to Automatix, not to reinstalling kde.  You're trying to install Automatix without adding its public key.

You want to type in "sudo aptitude install **kubuntu**-desktop" not **xubuntu**-desktop if you want kde to be installed.

---

### Post by jackrobinson on 2007-03-13
> **PurplePenguin said:**
> That problem is related to Automatix, not to reinstalling kde.  You're trying to install Automatix without adding its public key.

You want to type in "sudo aptitude install **kubuntu**-desktop" not **xubuntu**-desktop if you want kde to be installed.
The automatix GPG key issue is not critical. Running automatix for the first time, imports and adds all required keys.

---

