---
title: "Automatix and Opera on Edgy"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Nightmist on 2007-01-24
Hello,

I just installed Kubuntu 6.10 and am in the process of adding software and drivers I need/want. I tried Automatix, but didn't find Opera anywhere. Do I need to do something to install it? Is there another way to install opera? Like apt-get or Adept somehow?

Thanks.

---

### Post by Zzl1xndd on 2007-01-24
Opera should be listed in the internet section automatix. although I never use Kubuntu but I would think it should be the same.

---

### Post by xpod on 2007-01-24
You can also download the required version from their site i believe:D

EDIT:opera that is

---

### Post by youthforlinux on 2007-01-24
Okay here's the way

```
gksudo gedit /etc/apt/sources.list
```

paste that command into the terminal
when gedit opens

paste

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

to the bottom of the file

then save and exit

go to the terminal

type in 

```
sudo apt-get update
```

```
sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
sudo gpg --fingerprint 6A423791
sudo gpg --armor --export  6A423791| sudo apt-key add -
```

```
sudo apt-get install opera-static
```


If you still have problems check out the entry at the ubuntu wiki at: [https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

---

### Post by Nightmist on 2007-01-24
> **tweakedenigma said:**
> Opera should be listed in the internet section automatix. although I never use Kubuntu but I would think it should be the same.

That's what I thought, but it's not there.

---

### Post by Nightmist on 2007-01-24
> **xpod said:**
> You can also download the required version from their site i believe:D

EDIT:opera that is

Yeah, I'm keeping the "Windows way" of installing stuff as my last resort ;)

---

### Post by Nightmist on 2007-01-24
> **youthforlinux said:**
> Okay here's the way

```
gksudo gedit /etc/apt/sources.list
```

paste that command into the terminal
when gedit opens

paste

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

to the bottom of the file

then save and exit

go to the terminal

type in 

```
sudo apt-get update
```

```
sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
sudo gpg --fingerprint 6A423791
sudo gpg --armor --export  6A423791| sudo apt-key add -
```

```
sudo apt-get install opera-static
```


If you still have problems check out the entry at the ubuntu wiki at: [https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

Thanks for the help. But I get the following message when doing the update:

Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/binary-amd64/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found

Is it down or something?

EDIT: I checked the URL, and apparently there is no 64 bit version. What do I do to get apt to get another version (i386?)?

---

### Post by Quillz on 2007-01-24
I just checked Automatix, and Opera is there. I don't know why it isn't for you. I would just get the .deb package from their web site. When you go there, it should already automatically be selected for you.

---

### Post by Nightmist on 2007-01-24
> **Quillz said:**
> I just checked Automatix, and Opera is there. I don't know why it isn't for you. I would just get the .deb package from their web site. When you go there, it should already automatically be selected for you.

Here is my Automatix list:
[http://img178.imageshack.us/img178/5231/snapshot19oy.png](http://img178.imageshack.us/img178/5231/snapshot19oy.png)

I have no idea why it is missing. But I guess I will do as you suggest. Is there anything special to think about when installing it manually?

---

### Post by Quillz on 2007-01-24
> **Nightmist said:**
> Here is my Automatix list:
[http://img178.imageshack.us/img178/5231/snapshot19oy.png](http://img178.imageshack.us/img178/5231/snapshot19oy.png)

I have no idea why it is missing. But I guess I will do as you suggest. Is there anything special to think about when installing it manually?
No, it's almost exactly like using the package manager. Just download the .deb, double-click it and it will do the rest.

---

### Post by xpod on 2007-01-24
> Yeah, I'm keeping the "Windows way" of installing stuff as my last resort 

That certainly makes a change from all the folks whining cause nothing they click on downloads:D  Visiting sites may well be a Windows way but it`s also a good way for many ubuntu apps too.

After all, ANY way you can get what you want is a good way is it not:D

---

### Post by Nightmist on 2007-01-24
> **Quillz said:**
> No, it's almost exactly like using the package manager. Just download the .deb, double-click it and it will do the rest.

Thanks for your help.

Unfortunately, I get this message:

package architecture (i386) does not match system (amd64)

Am I screwed since I installed the 64 bit version of Kubuntu?

---

### Post by Nightmist on 2007-01-24
> **xpod said:**
> That certainly makes a change from all the folks whining cause nothing they click on downloads:D  Visiting sites may well be a Windows way but it`s also a good way for many ubuntu apps too.

After all, ANY way you can get what you want is a good way is it not:D

Hehe, well... I may be a Linux newb, but my first distro was Gentoo... so I'm sort of used to doing it that way ;)

---

### Post by hyper_ch on 2007-01-24
Opera can also be found in the canoncial repos.

Add the following line to your sources.list

```

deb http://archive.canonical.com/ubuntu edgy-commercial main

```

---

### Post by Quillz on 2007-01-24
> **Nightmist said:**
> Thanks for your help.

Unfortunately, I get this message:

package architecture (i386) does not match system (amd64)

Am I screwed since I installed the 64 bit version of Kubuntu?
Ahh... That could be it. Opera 9.1 may not yet be available to x86-64 users. Obviously, the problem with the .deb you got from Opera's site is that it only works on 32-bit processors, not 64-bit. Chances are, Automatix only loaded 64-bit software for you to use.

---

### Post by Nightmist on 2007-01-24
> **sjau said:**
> Opera can also be found in the canoncial repos.

Add the following line to your sources.list

```

deb http://archive.canonical.com/ubuntu edgy-commercial main

```

I thought the canonical repos. didn't "work" for edgy yet?

---

### Post by hyper_ch on 2007-01-24
Well, it works for me... however I just noticed I also have this repo:

```

deb http://archive.canonical.com/ edgy-commercial main

```

Now I'm kind of curious which one is the correct one :)

---

### Post by Nightmist on 2007-01-24
> **Quillz said:**
> Ahh... That could be it. Opera 9.1 may not yet be available to x86-64 users. Obviously, the problem with the .deb you got from Opera's site is that it only works on 32-bit processors, not 64-bit. Chances are, Automatix only loaded 64-bit software for you to use.

Ah, bugger. I found this guide to use 32 bit apps, but this is WAY over my head. Maybe if someone could write down all the exact command lines I would dare it, but like it is now I didn't understand much about the $'s and such @_@

---

### Post by youthforlinux on 2007-01-24
It only looks like Opera 9 will work for the i386, PPC , and Sparc Architechtures

And on ubuntuguide.org this is the only tutorial:

```
sudo apt-get install libqt3-mt
wget http://ftp.wayne.edu/opera/linux/910/final/en/i386/shared/opera_9.10-20061214.6-shared-qt_en_i386.deb
sudo dpkg -i opera_9.10-20061214.6-shared-qt_en_i386.deb
```

---

### Post by Nightmist on 2007-01-24
To enjoy and use internet properly I need Opera and I need the flash-plugin, neither of which are 64 bit. So I think I have to bite the apple and re-install Kubuntu i386 instead.

Maybe I could somehow find a way to run them if I was an expert, but I want to spend more time using Linux than to configure it :)

---

