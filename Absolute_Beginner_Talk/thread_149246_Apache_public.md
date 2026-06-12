---
title: "Apache public"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by mackyman on 2006-03-23
I have tried to get my apache server go public, and it was no problem in windows, but now, I can't get how I shuld do it...

Any ideas where I can find how to config it correctly? Or what I shuld do?
I haven't done too many changes from the common config...

Many thanks//

Mackyman

---

### Post by ranf on 2006-03-24
Have checked that you can access the HTTP server locally?
[http://localhost](http://localhost)

How are you connected to the Internet?

---

### Post by insub2 on 2007-09-15
I am having this same problem and yes, i can access [http://localhost](http://localhost).

I know it is an issue of setting *something* to be readable by the public.  but i have no idea what that *something* is.

please help.

---

### Post by ranf on 2007-09-16
Look for portforwarding in your router's setup. You need to forward port 80 to the IP address of your computer.

---

### Post by mackyman on 2007-09-16
I solved this after some work.

Checklist are:

1. Check so that you portforward port 80 ( if you are using port 80 on apache ) on your router

2. Yes, this is irritating to hear, but check your internet connection, can you really connect to the internet ( It's easy to forget a calble if you are moving the often )

3. Let someone else try to connect to your server "from the outside", some routers don't allow trafic to go local->public->local ( ie, you enter your ip so that you just go outside and back ), one example of this is smoothwall

Good luck and let us know how things are going//

Mackyman

---

