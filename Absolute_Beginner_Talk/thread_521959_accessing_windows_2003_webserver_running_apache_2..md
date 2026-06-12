---
title: "accessing windows 2003 webserver running apache 2.2 using ubuntu SLOOOOOOW slow!"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by seng1978 on 2007-08-09
Hi people,

I am running a windows 2003 web email server for almost a year now. My server is colocated with an Up/Downstream of 10MBit/s. While I was still using windows XP i could access my web pages and email within seconds no matter if I use IE or Mozilla. 
A week ago I gave Ubuntu a shot. Everything good so far. However, no matter if I use Mozilla or Netscape or Epiphany Web Browser they all access my web sites SLOW!!!!
The weird part is, accessing other web site such as Ubtuntu, Microsoft, Yahooo, Google, etc super fast.
So whenever i wanna access my website i got to use one of the other computers in my office running windows. We all use the same DSL connection by the way.

U smart guys got any solutions?:lolflag:

---

### Post by DSn0wMan on 2007-08-10
Many times a slow responding webserver can be traced back to a DNS problem. Is it faster if you hit the site from your loopback (127.0.0.1) ?

---

### Post by seng1978 on 2007-08-10
Thats what I thought too and I tried accessing the ip adress itself.
Nope.
I have six different DN's running on the web server. DN are registered over three different companies(go daddy, cnnames.net and ORAY). It must be my web server as you said responding slower to ubuntu requests.
Thanks for reply, I really appreciate it.

---

### Post by DSn0wMan on 2007-08-10
You might want to ask the guys in servers & security forum - [http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

My best guess is either something in your bind config, or your virtual server config is holding things up.

From most of my experience with apache2 it runs quite fast on ubuntu.

---

