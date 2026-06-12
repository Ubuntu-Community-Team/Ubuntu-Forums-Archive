---
title: "&quot;deb&quot; is blocking.."
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Pindulet on 2007-04-25
When I try to install or update anything I get this output:

```
E: the type ' "deb' is unknown on line 48 in the sourcelist /etc/apt/sources.list
```

The problem started after I tried to install automatix2. 
If I write:
```

nano /etc/apt/sources.list
```

I can see this output wich I believe is the problem:
```

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
[B]“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) Feisty main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) Feisty main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main[/B]

```
My problem is that I for some reason don't have permission to delete the automatixpart 

```
[ Error writing /etc/apt/sources.list: Permission denied ]

```

hope someone can help

K

---

### Post by taurus on 2007-04-25
You have four lines for the same thing, Aumatix.  Therefore, you need to edit /etc/apt/sources.list remove these three lines from it.

```

&#8220;deb http://www.getautomatix.com/apt Feisty main&#8221;
deb http://www.getautomatix.com/apt feisty main
&#8220;deb http://www.getautomatix.com/apt Feisty main&#8221;

```

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Pindulet on 2007-04-25
Thanks.. but the problem is, that when I delete the three lines and saves I get this output:
```

[ Error writing /etc/apt/sources.list: Permission denied ]
```

---

### Post by taurus on 2007-04-25
Please use the last command from my previous post to edit your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Pindulet on 2007-04-25
That worked.. :D

Thanks alot

---

