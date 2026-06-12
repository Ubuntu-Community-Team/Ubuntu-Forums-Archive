---
title: "to install ymessenger"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by jamadan on 2006-09-15
i have download yahoo messenger for ubuntu/debian linux. while to install (with sudo) the fail messege there...."need some pakage ..like lib something."
how to get that dependent? then ask me to resolve breaking package..etc.
need help.
tq

---

### Post by deadgobby on 2006-09-15
The Yahoo messager for linux kinda sucks. You can use GAIM and is way better than Y.M. for Linux. It is a snap it set it up and works very well. It has Yahoo, AIM, and other chitty chat instant pestering.
Gobby

---

### Post by Najand on 2006-09-15
I am afraid it is libssl0.9.6. It is SSL shared libraries (old version) and not available at Dapper Drake, because it is an old library. However you can download and install it from Ubuntu Package Contents Homepage before installing :
[http://packages.ubuntulinux.org/breezy/oldlibs/libssl0.9.6]("http://packages.ubuntulinux.org/breezy/oldlibs/libssl0.9.6")

Then install ymessenger and I think it will work after that.
You can use 
```

sudo dpkg -i <path>/<package name>

```
to install deb packages.

---

### Post by jamadan on 2006-09-15
> **deadgobby said:**
> The Yahoo messager for linux kinda sucks. You can use GAIM and is way better than Y.M. for Linux. It is a snap it set it up and works very well. It has Yahoo, AIM, and other chitty chat instant pestering.
Gobby

'Gaim'. I  try several time login using it fo my yahoo and msn messegenger before. but stil error messege from their server. so i dl ym.

anyway..i'll try to connect again.
tq

---

### Post by deadgobby on 2006-09-15
Are you using your sign in name like. [email]MEBAD@YAHOO.COM[/email] and enter your pass word?
 With yahoo, do not use @yahoo.com just use your use name and enter password.
Gobby

---

### Post by Najand on 2006-09-15
About Gaim, if you don't have the lastest version installed, upgrade it to the  lasted version. If you are via a proxy server. set your proxy at:
Gaim ->  Preferences -> Network
and write down your proxy address and your proxy port name.

---

### Post by rick_1010 on 2006-09-17
When I first started using GAIM I thought it was great because I could have all my messenger IDs on one piece of software. However, soon after starting to use it I ran into a few problems, one was that it would just delete at random all of the messenger IDs in my list (I know that it doesn't automatically show offline IDs, this wasn't the issue), then it started at times not showing a person as online when they were online.

After this I quickly figured out how to install yahoo messenger and I don't see whats bad about it, it has basically all the same features as in Windows (except I'm not sure about voice, I haven't checked on this yet), the graphics aren't quite as good but at least you don't have to worry about it having some bug that will just delete all your names, etc.

Anyways, I still have to use GAIM if I want to access the MSN network and it seems to work ok for this.

---

### Post by GStubbs43 on 2006-09-18
Look into a howto here  for gYachi... it is basically just like Y! Messenger.
I'll try to get a link...O:)

---

### Post by GStubbs43 on 2006-09-18
here ya go:
[http://ubuntuforums.org/showthread.php?t=190900](http://ubuntuforums.org/showthread.php?t=190900)

---

### Post by GoneWithTheWind on 2006-09-24
> **rick_1010 said:**
> After this I quickly figured out how to install yahoo messenger and I don't see whats bad about it, it has basically all the same features as in Windows

Can you use ytunnel, to block out the ads or what do you use for that?

I'm using yahoo 5.6.0.1358 on xp, so if could use the same on unbundu this would be cool.

Gaim is nice but is very basic, doesn't seperate messages etc.

---

### Post by ayllu on 2006-10-14
I have a problem installing ymessenger i get error dependence with xlibs, I dont know whats libs to dowload I traying to find in google but i cudnt. I dont know if a new version of gaim witch souport voice if some one konw what software i can use for supproting voice whit MSN or yahoo Messeger tell me.

---

### Post by meng on 2006-10-14
As other posters have said, ymessenger is pretty much a waste of time. It's an extremely old version and is outclassed by other open source alternatives.

---

### Post by ayllu on 2006-10-14
Hi... I found Gaim-vv that supoert vocie and video, but i cannot isntall it if someone knows hot to installit tellme please

([http://gaim-vv.sourceforge.net/](http://gaim-vv.sourceforge.net/))

---

