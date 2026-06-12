---
title: "In this thread we ask about apt"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by underwater on 2006-03-27
I just wanted to start this thread for people to ask questions about apt.

I have a few myself


why does it seem like some programs I have to press Y on for them to install and others just go right ahead and install?

Why is it that when I apt-get update, some sources that I know are valid are ignored?

---

### Post by az on 2006-03-27
Things in main should be packaged so that you don't have to press yes.  Things in universe may not be configured as such.

If one package forces the removal of another package, the default behaviour is to not install the first package.

---

### Post by aysiu on 2006-03-27
[QUOTE=underwater]
why does it seem like some programs I have to press Y on for them to install and others just go right ahead and install?[/quote] You can "solve" this by doing ```
sudo apt-get -y install packagename
```

> 
Why is it that when I apt-get update, some sources that I know are valid are ignored? Maybe they're commented out. Check your /etc/apt/sources.list--are there # signs in front of repositories?

---

