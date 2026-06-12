---
title: "internet only connecting to ubuntu sites"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by jonprc on 2006-07-31
hello,

i installed ubuntu a couple days ago with no problems. but everytime i try to use my wireless connection i'm only able to connect to ubuntu.com and anything from their site.

is there some simple setting i've overlooked that's locked me into their domain?
i havent touched anything in the DNS servers, search domains, or hosts sections. is there some tweaking that should occur there?

thanks for any help offered.
jon

---

### Post by Skia_42 on 2006-07-31
Are you sure you are going to an actual website? The default web page browsers go to is: > file:///usr/share/ubuntu-artwork/home/index.html
Notice that this is a web page coming from your computer not the internet. (it starts off with "file://", not "http://" You need to configure your internet.

---

### Post by jonprc on 2006-07-31
definitely connecting to the http ubuntu sites.
also, the automatic updates are downloading fine.

---

### Post by Titus A Duxass on 2006-07-31
Can you ping [www.google.com](www.google.com) in a terminal?

---

### Post by jonprc on 2006-07-31
yes, i do get a respsonse from google when i ping it

---

