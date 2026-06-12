---
title: "Stuck......."
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-25
Why won't this command work when I type it into the terminal?

> /usr/share/doc/cupsys/README.Debian.gz

Help?? What do I need to do to make it work?

---

### Post by taurus on 2006-07-25
You can't execute that thing!  It's a readme file so you need to read it...  Do something like this.

```

mkdir ~/temp
cp /usr/share/doc/cupsys/README.Debian.gz ~/temp
cd ~/temp
gzip -d README.Debian.gz
more README.Debian

```

---

### Post by cantormath on 2006-07-25
> **dragon1964m said:**
> Why won't this command work when I type it into the terminal?



Help?? What do I need to do to make it work?

because its not a command.

$ [fill in the blank] /usr/share/doc/cupsys/README.Debian.gz

---

### Post by dragon1964m on 2006-07-25
> **cantormath said:**
> because its not a command.

$ [fill in the blank] /usr/share/doc/cupsys/README.Debian.gz

Ok, what do I fill in the blank with?? Sorry if I seem dense. I have used Windows for more than 10 years and Linux for less than five weeks. I don't know what to do.

---

### Post by kinematic on 2006-07-25
> **dragon1964m said:**
> Why won't this command work when I type it into the terminal?



Help?? What do I need to do to make it work?

](*,)

---

### Post by taurus on 2006-07-25
> **dragon1964m said:**
> Ok, what do I fill in the blank with?? Sorry if I seem dense. I have used Windows for more than 10 years and Linux for less than five weeks. I don't know what to do.
Just follow my post above!!!  ](*,)

---

### Post by dragon1964m on 2006-07-25
Thx that got it to work. :)

---

### Post by geco on 2006-07-25
```
less /usr/share/doc/cupsys/README.Debian.gz
```

---

### Post by cantormath on 2006-08-01
> **dragon1964m said:**
> Ok, what do I fill in the blank with?? Sorry if I seem dense. I have used Windows for more than 10 years and Linux for less than five weeks. I don't know what to do.

Dont even trip, we were all there once upon a time.  Everyone is someones noob.

---

