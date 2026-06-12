---
title: "Setting up Wine"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Entase on 2006-12-19
Hi,

I ve tried using Cedega to Run WoW, but its so way too slow, and Ive heard good thinga about Wine, so I thought I might give it a try, but the problem is, I just really dont understand any of the HOWTOs Ive seen, could someone either direct me to a very, very simple How to, or just tell me how to do it, thanks.

---

### Post by pay on 2006-12-19
What stage are you at? Installing Wine or installing WoW? If you already have it installed from Cedega, then you probably can just use that installation with Wine.```
wine /path/to/wow.exe -opengl
```

---

### Post by Entase on 2006-12-19
No,

I have no idea how to even start, please just, does anyone know of a very, very simple guide to downloading, installing and configuring wine for WoW?

---

### Post by pay on 2006-12-19
```
nano /etc/apt/sources.list
```and add this at the end```
deb http://wine.budgetdedicated.com/apt edgy main
```then```
sudo aptitude update
sudo aptitude install wine
```

---

### Post by Rojahon on 2006-12-29
> **pay said:**
> ```
nano /etc/apt/sources.list
```and add this at the end```
deb http://wine.budgetdedicated.com/apt edgy main
```then```
sudo aptitude update
sudo aptitude install wine
```

When I do
```
sudo aptitude update
```
I get an error saying:
```
Err http://wine.budgetdedicated.com edgy/main Translation-en_US                 
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
```

Any idea why?

---

### Post by Jussi01 on 2006-12-29
> **Entase said:**
> No,

I have no idea how to even start, please just, does anyone know of a very, very simple guide to downloading, installing and configuring wine for WoW?


If your after simple - go to [www.codewaeavers.com](www.codewaeavers.com) pay your $40 and get crossoveroffice. this program has a very windows like install for WoW.

---

### Post by Ramses de Norre on 2006-12-29
It seems like their repo is down.. I can't connect to any of their debian repos..
Waiting untill it's finished will be the only solution I guess..

---

