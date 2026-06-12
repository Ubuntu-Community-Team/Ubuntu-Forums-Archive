---
title: "Determine Internet Speed from Terminal"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-03-29
Cheers,

I was wondering if it is possible to determine the speed of the Internet Bandwidth from the Terminal.  I usually monitor my home pc (Ubuntu Edgy) from the office via ssh, and I want to know the speed of my Internet if possible.

Thanks.

---

### Post by aparigraha on 2007-03-29
yeah... would really like to be able to do that as well.

---

### Post by oilchangeguy on 2007-03-29
you can check the speed of your internet connection at [www.speakeasy.net](www.speakeasy.net)

---

### Post by aparigraha on 2007-03-29
well thx... but not really the issue here. i think we are both talking about monitoring real-time bandwith usage

---

### Post by aparigraha on 2007-03-29
actually poked around a bit and found **[COLOR="Red"]dstat[/COLOR]**.
before u try it, have a look here:

[http://dag.wieers.com/home-made/dstat/]("http://dag.wieers.com/home-made/dstat/")

suits me perfectly and easy to install

```
sudo apt-get install dstat
```

i run it with ```
dstat -n 5
```
to get a 5 sec average

GREAT TOOL!

---

### Post by delphiguy on 2007-03-29
Wow, it is possible after all.
dstat is exactly what I'm looking for.

thanks a lot for the help.

---

### Post by halitech on 2007-03-29
bumping this so I can do it later as well :)

---

