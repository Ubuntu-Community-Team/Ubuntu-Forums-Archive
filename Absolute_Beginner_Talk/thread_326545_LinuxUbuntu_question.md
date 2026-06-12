---
title: "Linux/Ubuntu question"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by ColdFront on 2006-12-27
Hey all, my name is Rj and I just installed Ubuntu today on one of my machines.  I thought it was finally time I started to teach myself something other then Windows.  

Anyways, I have what is probly a pretty stupid question.  How do I open a .bin file?  I am trying to install a couple programs that were made for Linux and I can't seem to be able to figure it out.  

I'm sure this is prob only 1 question I will have out of many in the future.  

Thanks in advance.  

Rj

---

### Post by habtish on 2006-12-27
I could be wrong on this but I think .bin files are binaries that usually reside in /bin or /usr/bin.
Trying to install your programs using Synaptic (System>Adminstration>synaptic) provided they are in the ubuntu repositories and you have enabled extra Repos. I would also recommend [Ubuntuguide ]("http://ubuntuguide.org")if you like using the terminal. You can get lots of pointers on how to install a essential apps there

---

### Post by jvc26 on 2006-12-27
Hey mate, just a couple of things,
1/ Synaptic offers the best way for installing things easily for more info on installing a rather large range of things from synaptic check out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
2/ For installing things such as .bin files this guide always comes in handy for a new user:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Your .bin file on your desktop the easiest way to install it is to Right click, properties, permissions, make executable, then double click on it or from terminal
```

cd /home/USER/Desktop
filename.bin

```

Il

---

### Post by wpshooter on 2006-12-27
at the terminal get to the directory where you have the file located and then try

chmod +x followed by your binary file name.

I think this will make it executable.

---

### Post by jvc26 on 2006-12-27
The chmod command will work, but it is probably infinitely more simple to go for the right click, permissions approach - you may well be able to find the package in synaptic before you install it though, so it will probably be worth checking out ubuntu guide and so forth to see whether you're trying to install a package which is already in the repositories.
Il

---

### Post by wpshooter on 2006-12-27
> **Illuvator said:**
> The chmod command will work, but it is probably infinitely more simple to go for the right click, permissions approach - you may well be able to find the package in synaptic before you install it though, so it will probably be worth checking out ubuntu guide and so forth to see whether you're trying to install a package which is already in the repositories.
Il

Yes, I **completel**y agree.  If the software is available thru Synaptic, that is **the way** to install it.

---

### Post by Sef on 2006-12-27
> Anyways, I have what is probly a pretty stupid question

No, it was not a stupid question.   It is much better to ask and learn than flail around in ignorance.

---

