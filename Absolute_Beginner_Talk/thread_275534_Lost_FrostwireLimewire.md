---
title: "Lost Frostwire/Limewire"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-10-11
This will sound weird I'm sure but, I remember having the option to install Frostwire from the "add/remove" feature, and I'm pretty sure that Limewire was in there too. Now however, they don't show up in the internet section of the add/remove app at all, and am wondering where they might have gotten to ? Anyone have any ideas as to what I can do to get them back ? 

The only thing I can think of that might have had an impact was when I installed Automatix and allowed it to change the repository settings. Since then though, I've reverted back to the original ones, but that hasn't fixed my issue. 

Doug

---

### Post by _lynX on 2006-10-11
> **Sweet Spot said:**
> This will sound weird I'm sure but, I remember having the option to install Frostwire from the "add/remove" feature, and I'm pretty sure that Limewire was in there too. Now however, they don't show up in the internet section of the add/remove app at all, and am wondering where they might have gotten to ? Anyone have any ideas as to what I can do to get them back ? 

The only thing I can think of that might have had an impact was when I installed Automatix and allowed it to change the repository settings. Since then though, I've reverted back to the original ones, but that hasn't fixed my issue. 

Doug

Open up a console and try *sudo apt-get install frostwire*. I'm not sure why Frostwire has disappeared from Add/Remove Apps.

---

### Post by Sweet Spot on 2006-10-11
Hmm. I tried that, and got this: > Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package frostwire


Working for you I take it ?

---

### Post by smartalecks on 2006-10-11
Are you sure that you installed it via Synaptic and not Automatix? If you did, then you have probably lost a repository or they have removed it from a repo.

---

### Post by Sweet Spot on 2006-10-11
By "it", I take it you mean Frostwire ? The first time I installed it, was through the Add/Remove programs app, as I said above. But the stuff in the add/remove app depends on what's found in the synaptic list, which depends on the repository list, correct ?  Can you confirm whether or not you have the option to install it from add/remove please ? 

Doug

---

### Post by taurus on 2006-10-11
If you want to install frostwire and it's not in your repos, then just download it and install it by hand...

[http://www.frostwire.com/](http://www.frostwire.com/)

```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```

---

### Post by Sweet Spot on 2006-10-11
It would be really helpful to know if any of the methods recommended by you guys is actually working for anyone. Reason being:

> dpkg: error processing FrostWire-4.10.9-2.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 FrostWire-4.10.9-2.i586.deb


So that makes the count 0 and 2  ](*,)

Doug

---

### Post by taurus on 2006-10-11
If you downloaded from the link that I gave you, then chances are it will be in ~/Desktop!  Therefore, you need to change to that directory first before you can install it...  Open a terminal, Applications -> Accessories -> Terminal, and type

```

cd ~/Desktop
sudo dpkg -i FrostWire-4.10.9-2.i586.deb

```
Then, you will find it under Applications -> Internet -> Frostwire.

---

### Post by Sweet Spot on 2006-10-12
Possibly fixed...

Yes, it's good, thank you. I didn't actually need the first part as the deb package just appeared on my desktop, but thank you. 

Now though, I'd really STILL like to know why I can't see it in my add/remove program list, or if it's been taken out of the repository list ?  

Doug

---

### Post by taurus on 2006-10-12
Not sure but maybe because it's in the universe/multiverse and you don't have to "activate" in your /etc/apt/sources.list!!!

---

### Post by Irish J on 2006-10-12
Frostwire/Limewire kept hanging on me.  GTK-Gnutella for the win!

sudo apt-get install gtk-gnutella

---

### Post by taurus on 2006-10-12
> **Irish J said:**
> Frostwire/Limewire kept hanging on me.  GTK-Gnutella for the win!
Maybe because of java!!!

---

### Post by TheRingmaster on 2006-11-09
is there a special repo that is just for frostwire, so that I can put it into my sources.list?

edit: I just installed the .deb file from there official site and I found it in applications-->internet-->frostwire. I clicked on it and nothing happened. I have the latest version of java. so what is the deal?

---

### Post by taurus on 2006-11-09
> **TheRingmaster said:**
> is there a special repo that is just for frostwire, so that I can put it into my sources.list?

edit: I just installed the .deb file from there official site and I found it in applications-->internet-->frostwire. I clicked on it and nothing happened. I have the latest version of java. so what is the deal?
Try to run it from a terminal to see exactly what the error message is, Applications -> Accessories -> Terminal.

```
frostwire
```

---

### Post by Midway on 2006-11-09
I don't remember seeing it in add/remove but I installed mine thru Automatix2.

---

### Post by TheRingmaster on 2006-11-09
> **taurus said:**
> Try to run it from a terminal to see exactly what the error message is, Applications -> Accessories -> Terminal.

```
frostwire
```


it says: ```
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

```

---

### Post by taurus on 2006-11-09
Look in /usr/bin/frostwire, change the sh to bash...

```
gksudo gedit /usr/bin/frostwire
```

---

### Post by TheRingmaster on 2006-11-09
> **taurus said:**
> Look in /usr/bin/frostwire, change the sh to bash...

```
gksudo gedit /usr/bin/frostwire
```
> #!/bin/bash
cd /usr/lib/frostwire
sh runFrost.sh


which one?

---

### Post by taurus on 2006-11-09
Change the last line to look like this.

```
bash runFrost.sh
```

---

### Post by TheRingmaster on 2006-11-09
thanks again taurus!

---

### Post by taurus on 2006-11-09
> **TheRingmaster said:**
> thanks again taurus!
I take it it works now!!!  ;)

---

### Post by TheRingmaster on 2006-11-09
like a charm :)

---

### Post by taurus on 2006-11-09
> **TheRingmaster said:**
> like a charm :)
Good.  Have fun...

---

