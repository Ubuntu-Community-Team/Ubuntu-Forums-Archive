---
title: "search with apt-get"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-03-19
Hi – how do I search with apt-get? I need to download some C compilers but I don't know which , is there some way that apt-get will tell me which C compilers are available in the repositories ? I know I can use synaptic , I was just wondering...

---

### Post by mcduck on 2006-03-19
[QUOTE=seshomaru samma]Hi – how do I search with apt-get? I need to download some C compilers but I don't know which , is there some way that apt-get will tell me which C compilers are available in the repositories ? I know I can use synaptic , I was just wondering...[/QUOTE]
it's possible. First do 'sudo apt-get update', and then you can use 'apt-cache search <packagename>' to search packages, and 'apt-cache show <packagename>' to show all information about a certain package..

---

### Post by Jucato on 2006-03-19
```
apt-cache search *search_pattern*
```

---

### Post by seshomaru samma on 2006-03-19
thanks , 
while we are on the subject of c compliers ,how do I know which compiler I need to compile [COLOR="Navy"]_[scim-anthy]("http://sourceforge.jp/projects/scim-imengine/") _[/COLOR]?

---

### Post by Jucato on 2006-03-19
I'm not sure if the default compiler that comes with Linux (gcc-3.4) is able to compile C++ code.

Off-topic: are you the brother of Inuyasha? :D

---

### Post by chuckyp on 2006-03-19
If you wish to install the most basic compilers which allow you to install most source code software.  You can install the meta package build-essential so you would just sudo apt-get install build-essential.  If you want to see what this package contains you can always apt-cache showpkg build-essential .

---

### Post by seshomaru samma on 2006-03-20
[QUOTE=Fenyx]I'm not sure if the default compiler that comes with Linux (gcc-3.4) is able to compile C++ code.

[/QUOTE]

It's not , I had to download the meta package build-essential (thanks chuckyp)
> 
Off-topic: are you the brother of Inuyasha? :D

I am ;)

---

