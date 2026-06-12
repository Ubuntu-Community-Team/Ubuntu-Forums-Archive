---
title: "help please!"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by nalap on 2008-02-24
I am haveing a computer built but we are both new to this stuff and the person helping can't answer our questions so I thought I would try here.
we are looking for certain programs for the Ubuntu system and we are not sure if the actually exist or where we would find them if they do.
we want 4 programes
one for music  - record and edit it 
one for art- making pictures 
one for photos- to change and edit the image
and one for making patterns for sewing projects
I hope that someone can help could you tell me where I might find any of this or if I can find any of this.

---

### Post by bcl1713 on 2008-02-24
audacity, gimp, gimp or fspot or picasa

---

### Post by PmDematagoda on 2008-02-24
> one for music - record and edit it 
Audacity is very good, it can be installed using:-
```
sudo apt-get install audacity
```

> one for art- making pictures 
GIMP is good for that, it can be installed using:-
```
sudo apt-get install gimp
```
but if you use Ubuntu then it is built-in and can be found in Applications>Graphics>GNU Image Manipulation Program.

> one for photos- to change and edit the image
F-Spot is rather good for this task and may be even GIMP could be used for that.
F-Spot can be installed using:-
```
sudo apt-get install f-spot
```

> and one for making patterns for sewing projects
I am not entirely sure about that, sorry.

---

### Post by oedha on 2008-02-24
edit : audacity

---

### Post by kooolrock on 2008-02-24
> **bcl1713 said:**
> audacity, gimp, gimp or fspot or picasa
waht is CLI for picassa?

---

### Post by bcl1713 on 2008-02-25
Its not available in repositories but you can download debs from [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

---

### Post by FoolsRun on 2008-02-25
The sewing patterns thing is tough; is there a Windows equivalent program? Sometimes Linux alternatives can be found by googling "linux [name of Windows software]", as oft-times the smarter Linux devs with make reference to the Windows tools to help new users find their software.

---

### Post by osx424242 on 2008-02-25
Hi Nalap,

You didn't say: do you currently use software to perform these tasks:

> **nalap said:**
> one for music  - record and edit it 
one for art- making pictures 
one for photos- to change and edit the image
and one for making patterns for sewing projects

If you tell us what programs you are currently using, people may be able to provide more targeted suggestions.

I'd also like to second The GIMP, it's a great program :)  It is also available for Windows and Mac OS X, if you are using either of those operating systems, see [www.gimp.org](www.gimp.org).

---

### Post by nalap on 2008-02-25
> **osx424242 said:**
> Hi Nalap,

You didn't say: do you currently use software to perform these tasks:

 [www.gimp.org](www.gimp.org).



No we donot currently have software to perform these tasks, we were asked to see if we could find the software that would, I know very little about most of these things so when I found this I thought it would be a better ides to ask those who might know as I have had very little luck searching the internet as I am not too sur what am searching for in words the searchengines will be able to provide me with an answer

---

### Post by tango_ninja on 2008-02-25
I would agree with everyone else....
[LIST]
[*]Audacity (for sound editing/recording)
[*]Gimp (for image editing)
[*]f-spot (for image organisation...i never could get Picasa working on linux...)
[/LIST]

what are your requirements for this sewing program? Would something simple like OpenOffice Draw work ???

---

### Post by tango_ninja on 2008-02-26
OK here's an update :)  I finally got Picasa (v2.7) working !!! It is now better than f-spot by far. Get rid of f-spot and install Picasa 2.7 (not 2.2, it stinks).

Here's how:

1) Add the Google beta repository:
```
# Google testing repository
deb http://dl.google.com/linux/deb/ testing non-free 
```

2) Add the Google package signing key, found here : [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub)

3) ```
sudo apt-get install picasa
```

---

