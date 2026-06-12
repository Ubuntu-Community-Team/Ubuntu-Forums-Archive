---
title: "Problems locating programs"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by darkchest on 2006-06-24
I downloaded the desktop version from ubuntu site.

I wanted to use php.  I thought php, apache and mysql comes with most linux distros (if not all), but to my suprise i didnt see it in this version.  So i used the "synaptic package manager" to download them.  It was meant to install, but i looked for the apache folder, and i didnt see it.  So i decided to download apache from the site. 

I extracted the folder and did the "./configure" command.  What i could see was
"configure: error: no acceptable C compiler found in $PATH"

Wat d .... does that mean?  No C in ubuntu.  Someone pls tell me wats going on.

---

### Post by raptros-v76 on 2006-06-24
well. you need gcc for C compiling.

---

### Post by mlind on 2006-06-24
All that stuff is available on Ubuntu's repositories, but not installed by default like
it should be. Not many users use apache httpd or php anyway.

```

sudo aptitude install apache2 mysql-server php5

```

if you really wish to build apache httpd server yourself, install build-essential package
which provides gcc.

---

### Post by dmizer on 2006-06-24
there's not going to be a "folder" per se for apache or any of the others for that matter, all the server configuration is done through a browser window.

take a look at this site on how to set things up:
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) ... scroll down toward the bottom of the contents and you'll find what you're looking for.

---

### Post by darkchest on 2006-06-25
Thanx dmizer, mlind, raptros-v76.  The link was really helpful.  You guys make it happen.

---

