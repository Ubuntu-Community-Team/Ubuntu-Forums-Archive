---
title: "can't upgrade or install files"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by stevensonfire on 2008-01-22
it keeps saying get-apt ir aptitude is running... which i believe is not because i restarted and to install updates i get dpkg was interrupted,
E: must manually run dpkg --configure -a to correct problem
E:_cache->open()failed
yea it prolly is a [insert obscenity] thing to fix
but any help would be appreciated...
ohh and what do i use to watch movies and stuff like that
i used the medibuntu to get the fiesty fox stuff
but i keep getting another file is open just frustrating

---

### Post by bump_ on 2008-01-22
Have you tried typing 
```
dpkg --configure -a
``` in the terminal?

Just in case, the terminal is found Applications -> Acessories -> Terminal

Edit: Also I use vlc player for movies. To get it, (after the above problem is resolved) just type 
```
sudo apt-get install vlc
```
in the terminal again.

---

### Post by Paul820 on 2008-01-22
Don't forget the sudo first, it needs to be root
> sudo dpkg --configure -a

---

### Post by bump_ on 2008-01-22
Ahh I always seem to be making these silly omissions or misspellings. Thank you Paul

---

### Post by stevensonfire on 2008-01-22
wow that was pretty obvious... haha thanks
i forgot the sudo when i tried that.. 
thanks

---

