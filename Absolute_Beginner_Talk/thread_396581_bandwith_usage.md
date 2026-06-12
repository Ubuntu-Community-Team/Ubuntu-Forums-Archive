---
title: "bandwith usage"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by aparigraha on 2007-03-29
Hopefully this is a simple yes or no...

I use a windows machine and PuTTY to connect to a ubuntu server. What I need to be able to do is to monitor the bandwidth usage through the terminal window... and maybe also to create a log of it. Can that be done? And if so - how?

---

### Post by aparigraha on 2007-03-29
nevermind....
actually poked around a bit and found **[COLOR="Red"]dstat[/COLOR]**.
before u try it, have a look here:

[http://dag.wieers.com/home-made/dstat/]("http://dag.wieers.com/home-made/dstat/")

suits me perfect and easy to install

```
sudo apt-get install dstat
```

i run it with ```
dstat -n 5
```
to get a 5 sec average

GREAT TOOL!

---

