---
title: "Opera for linux"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-12-24
Im planning on installing Opera in ubuntu, but when I view the Opera site I am given three choices for linux operating system; sparc, powerpc, and i386. I've only been using ubuntu for about 4 months now so im still feeling pretty noobish at this so which one am I supposed to d/l?

Im guessing its i386 but I just wanted to be sure. And what distros are the other two options for?

---

### Post by autocrosser on 2007-12-24
i386 is the correct choice--Powerpc is Apple (old style) & sparc is a offshoot you won't see much (you'll know if you have one ;)  )

Make sure you D/L the .deb file & just double-click it to install--a app called "gdebi' will open

---

### Post by forestpixie on 2007-12-24
you guessed right - but I'm not sure bout the other two

---

### Post by devosion on 2007-12-24
Thanks guys. Appreciate the assistance!

---

### Post by anubhavrocks on 2007-12-24
On the terminal give the following command
```
cat /proc/cpuinfo
```
The output will give you the information about the cpu.If its Intel or AMD use opera i386.

The SPARC and  POWERPC  are cpu architecture's which require their own version of software.

---

### Post by LaRoza on 2007-12-24
Get Opera 9.5b, otherwise Flash won't work. (Even though it is beta, it is good and mostly stable)

---

### Post by hyper_ch on 2007-12-24
Isn't Opera in the Canonical Partner repo?

Add this repo to your sources.list:
```

deb http://archive.canonical.com/ubuntu gutsy partner

```
I think Opera is in there.

If it is not, then it is in the Medibuntu repo. For that, visit [http://www.medibuntu.org](http://www.medibuntu.org) --> there's a howto on how to add.

---

### Post by devosion on 2007-12-24
> **hyper_ch said:**
> Isn't Opera in the Canonical Partner repo?

Add this repo to your sources.list:
```

deb http://archive.canonical.com/ubuntu gutsy partner

```
I think Opera is in there.

If it is not, then it is in the Medibuntu repo. For that, visit [http://www.medibuntu.org](http://www.medibuntu.org) --> there's a howto on how to add.

I'll give that a shot when I get home, and before I give the .deb package a whirl.

---

### Post by LaRoza on 2007-12-24
> **devosion said:**
> I'll give that a shot when I get home, and before I give the .deb package a whirl.

The .deb is no hassle. I don't know if the beta version will be in the repo, which I recommend you use.

(I don't normally recommend beta software, but there are special circumstances involved)

---

