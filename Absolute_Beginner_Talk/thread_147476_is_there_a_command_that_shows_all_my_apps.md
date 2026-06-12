---
title: "is there a command that shows all my apps?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-03-20
you know, for those days i want to make my own candles.

---

### Post by Gustav on 2006-03-20
You could use synaptic to see all your installed packages or you could just press tab in the terminal to see all availible commands. 

But there must be better ways than that to do this :)

---

### Post by mority on 2006-03-20
Well, this command (run it as root) would show pretty much all your applications (i.e. the executables running the applications), but I doubt that this makes much sense.
```

ls /bin && ls /sbin && ls /usr/bin && ls /usr/sbin && ls /usr/games

```

I did'nt get what exactly you are planning to do, but your question is answered :-k

---

### Post by timas on 2006-03-20
I can see this being useful on a server that needs to be mirrored.. I've had the issue where the previous maintainer installed the web server and I demanded a mirror of that machine that would be exactly the same.. I just had the trouble of not knowing what exactly was installed.. so a list of installed applications could in that case turn out rather handy..

---

### Post by fuscia on 2006-03-20
[QUOTE=mority]Well, this command (run it as root) would show pretty much all your applications (i.e. the executables running the applications), but I doubt that this makes much sense.
```

ls /bin && ls /sbin && ls /usr/bin && ls /usr/sbin && ls /usr/games

```[/quote]

thanks, that was what i wanted. it made plenty of sense.

---

### Post by mority on 2006-03-21
[QUOTE=fuscia]thanks, that was what i wanted. it made plenty of sense.[/QUOTE]

Fine. Glad to help :)

---

