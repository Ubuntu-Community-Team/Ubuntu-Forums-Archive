---
title: "Is there a standard location to put user shell scripts?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Barleyman on 2007-10-09
I usually put user shell scripts in /home/me/bin, is this the correct standard location?

---

### Post by hyper_ch on 2007-10-09
well, you can organize your home as you want to... if you want to make the shell script globally available then it's not a good location.

---

### Post by milosz.galazka on 2007-10-09
Hi, If you are only one person that uses it then you can use *PATH* variable.
Just look at output of ```
echo $PATH
``` and you will see standard locations of scripts/executables and to add new directory you could run command ```
export PATH="$PATH:/home/me/bin"
```

If everything is fine than you can add this command to *.bashrc* script or any other depending on shell you are using.

---

### Post by bodhi.zazen on 2007-10-09
~/bin is "standard"

---

### Post by milosz.galazka on 2007-10-09
> **bodhi.zazen said:**
> ~/bin is "standard"

I didn't know that :) and it is in the *PATH*, wow

---

### Post by Joeb454 on 2007-10-09
Any scripts I write just live in Home.

That way i just type ./scriptname though usually it's more like sudo ./sc *tab key*

I love autocomplete :p

---

### Post by jis on 2007-12-10
> **milosz.galazka said:**
> 
If everything is fine than you can add this command to *.bashrc* script or any other depending on shell you are using.

But .bashrc is in home folder. What if you want the path for all users?

---

### Post by ByteJuggler on 2007-12-10
> **jis said:**
> But .bashrc is in home folder. What if you want the path for all users?

Then edit /etc/profile

---

