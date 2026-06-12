---
title: "Neet to install &quot;libc&quot; from command prompt.  How?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Kerry Lange on 2007-02-03
Hi there:

I'm trying to install the latest nVidia drivers in Feisty and am told I need to install "libc" first.

Is this as simple as something like the following:

"sudo apt-get libc"?

Or what command will I need to use?

---

### Post by ovidescu on 2007-02-03
I use aptitude instead of apt-get, because of this:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

So your command would be
```
sudo aptitude install libc6
```
First, do a search in Synaptic for the package you want to install. I just looked libc up in the Synaptic repositories and there is no such package, but there is libc6 (so I guess that's what you want to install).

Ovidiu

---

### Post by po0f on 2007-02-03
Kerry Lange,

From a terminal:

```
[FONT="Courier New"]$ sudo aptitude install build-essential[/FONT]
```

---

### Post by Kerry Lange on 2007-02-04
All is good now!  I got the X server running.  Here's what worked:

sudo aptitude install libc6-dev

---

### Post by R.J.R. on 2007-02-04
I usually do a search first to see the libraries, then choose the closest one to what I need. I'm a noob but it's worked for me so far. 

```
sudo apt-cache search libX11 
```

---

### Post by Kerry Lange on 2007-02-05
> **R.J.R. said:**
> I usually do a search first to see the libraries, then choose the closest one to what I need. I'm a noob but it's worked for me so far. 

```
sudo apt-cache search libX11 
```

Thanks for the tip!  I'll try to remember that for the next time I'm stuck without the GDM.

---

