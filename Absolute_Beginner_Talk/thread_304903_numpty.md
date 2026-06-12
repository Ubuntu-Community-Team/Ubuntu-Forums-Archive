---
title: "numpty"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by externalsupport on 2006-11-22
Ok I'm officaially a numpty. Twice now I have screwed my ubuntu server installation by issuing the command sudo chmod 777 -R/var/www/work_area /* ](*,) 

Couple of questions.

1)is there anything I can do to recover from this ? I presed ctrl-c as soon as I had hit return but too late :-(

2) is there anything I can do to stop me from doing this? Is there anway I can trap a chmod command and get a prompt asking "Are yo sure [y/N]?

Thanks 

Ste

---

### Post by CatKiller on 2006-11-22
> **externalsupport said:**
> 2) is there anything I can do to stop me from doing this? Is there anway I can trap a chmod command and get a prompt asking "Are yo sure [y/N]?

That's quite an interesting idea. You might be able to use an alias in your ~/.bashrc file. More high-tech than a Post-It, I suppose.

---

### Post by bodhi.zazen on 2006-11-22
You could easily write a short bash script using zenity asking for confirmation before you chmod.

You can then add it to ~/.bashrc as a function.

---

### Post by externalsupport on 2006-11-22
thanks for the replies. I am a relative noob and have no experience of writing scripts. Are there any tutorials out there?

Ste

---

### Post by bodhi.zazen on 2006-11-22
> **externalsupport said:**
> thanks for the replies. I am a relative noob and have no experience of writing scripts. Are there any tutorials out there?

Ste

[This](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) is a place to start, although there are others...

The script itself would be very short, I will look at it as time allows.....

---

