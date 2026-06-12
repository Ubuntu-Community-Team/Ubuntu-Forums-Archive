---
title: "CloneCD in WINE"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-06-12
I have a .img, .ccd, and .sub file. I did some research and found they were the files that CloneCD uses. I'm trying to run CloneCD in WINE to burn it to a cd, but I'm getting this error message:

"Unable to load the CloneCD device driver!
AFter Installation of ClonceCE Windows has to be restarted"

I restarted Ubuntu, but that didn't work for me.

---

### Post by PMatt on 2007-06-12
Is there another program I could use to burn these files or convert them?

---

### Post by mrphantastic on 2007-06-12
hey, sorry to burst ur bubble, but i found a GREAT program, it's just not free...ugh.  here it is.  [http://www.nero.com/eng/NeroLINUX.html]("http://www.nero.com/eng/NeroLINUX.html")  Yeah, they actually make a version of nero, that i think runs on ubuntu.  I am thinking u can get a trial version, check out that site though.  Good luck.  That's like, all i found.

---

### Post by machoo02 on 2007-06-12
Check out [MountISO]("http://www.kde-apps.org/content/show.php?content=11577&forumpage=13&PHPSESSID=74796ae42c06099fff7eacd34bd9de65")...it  might be what you are looking for.  Also, look at [ccd2iso,]("http://sourceforge.net/projects/ccd2iso/") which is a converter program available in the repos.

---

### Post by PMatt on 2007-06-12
> **machoo02 said:**
> Check out [MountISO]("http://www.kde-apps.org/content/show.php?content=11577&forumpage=13&PHPSESSID=74796ae42c06099fff7eacd34bd9de65")...it  might be what you are looking for.  Also, look at [ccd2iso,]("http://sourceforge.net/projects/ccd2iso/") which is a converter program available in the repos.

I got ccd2iso, but I'm unsure how to install it.

---

### Post by machoo02 on 2007-06-12
Make sure you have the universe repository enabled, and you can install it with```
sudo aptitude install ccd2iso
```

---

