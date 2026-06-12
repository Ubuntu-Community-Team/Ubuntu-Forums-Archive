---
title: "[SOLVED] How to install both Ubuntu &amp;amp; Kubuntu? And how to install beryl on Kubuntu?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by amyst on 2007-11-24
Does anyone know if it is possible to install both Ubuntu and Kubuntu on different hard drive partitions? If the swap and the root of a Kubuntu are installed in the two logical partitions of an extended partition that is divided into three logical partitions, is it possible to install Ubuntu on the third logical partition and have Kubuntu and Ubuntu sharing the same swap partition?

Is installation of Beryl follow the same procedure as in Kubuntu? I read the online Ubuntu documentation and tried: 

sudo aptitude update
sudo aptitude install beryl emerald-themes

but can't download any package! I went to [url/packages.ubuntu.com/feisty/x11/beryl-kubuntu[/url] and downloaded "beryl...all.deb". I got an "... no dependency..." error during installation :(. Does anyone know what I might have missed?

---

### Post by Flying caveman on 2007-11-24
you can have both kubuntu and ubuntu on the same partition just change the session at the login screen. 

```
sudo apt-get install kubuntu-desktop
```

Why make it more complicated than it is?

......But I suppose you could put it on a seperate partition.

---

### Post by amyst on 2008-02-19
Sorry about this late thank you. Forgive me I'm a green user.

Thanks!

---

### Post by oedha on 2008-02-19
follow what flying caveman said ( easier one )
and i want to add that...you can install both of them on different partition...maximum = 4 ( my experience )

about beryl.......now we play compiz.......

---

### Post by hyper_ch on 2008-02-19
> **oedha said:**
> and i want to add that...you can install both of them on different partition...maximum = 4 ( my experience )

you can only have 4 primary partitions but you can create an extended one and partition it inside with logical ones.

---

### Post by oedha on 2008-02-19
thanks for the info.....
since i still use windows.....i usually put win on the primary...and the rest on extended/logical.......so so far...i always have 1 primary...:)

---

