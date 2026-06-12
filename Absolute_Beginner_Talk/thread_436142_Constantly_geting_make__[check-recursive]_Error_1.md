---
title: "Constantly geting: make: *** [check-recursive] Error 1"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by acompw on 2007-05-07
Okay - I'm not a Debian n00b per se but I seem to be having an issue compiling just about every program I had no issue compiling on pre-feisty releases.

make[1]: *** [check] Error 1
make[1]: Leaving directory `/home/user/Desktop/scribes-0.3.2.2/po'
make: *** [check-recursive] Error 1

I'm getting check-recursive errors on scribus....and when compiling pidgin (if someone has a list of ubuntu pkgs that will satisfy the dependencies for source install -- please share)

Thanks

---

### Post by aysiu on 2007-05-07
Wouldn't you get a list of dependencies by typing in this command? ```
sudo apt-get install scribus
``` You wouldn't have to go through with the *apt-get* command (you can always say "no"), but it would list Scribus' dependencies.

---

### Post by acompw on 2007-05-07
I wanted to install scribus from source


> **aysiu said:**
> Wouldn't you get a list of dependencies by typing in this command? ```
sudo apt-get install scribus
``` You wouldn't have to go through with the *apt-get* command (you can always say "no"), but it would list Scribus' dependencies.

---

### Post by aysiu on 2007-05-07
I know you do, but I'm saying that if you use the *apt-get* command, you can see what dependencies Scribus will need. You don't actually have to follow through with the command. You can say "no" when asked if you want to continue.

Alternatively, this could help you:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Bachstelze on 2007-05-07
What you've pasted does not help us to find out what the problem is, please paste the whole output of make.

---

