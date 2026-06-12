---
title: "internet problem"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-08-31
Hi.

On a school and i've got the ipadd and port for the internet, but cant get it to work in ubuntu. I connect to the internet but can browse the internet or download packages or anything. What to do ?

---

### Post by czepluch on 2007-08-31
BTW i use firefox

---

### Post by wormser on 2007-08-31
How do you know you are connected to the internet?  Try putting 82.211.81.186 in Firefox.  If it works then this is just a DNS issue.  Are you getting an IP address?  Applications> Accessories> Terminal.

```
ifconfig
```

It also could be a hardware issue.  Post the results of the command below.  If you can just post your network card and if you are unsure post the whole thing.

```
lspci
```

---

### Post by czepluch on 2007-08-31
> **wormser said:**
> How do you know you are connected to the internet?  Try putting 82.211.81.186 in Firefox.  If it works then this is just a DNS issue.  Are you getting an IP address?  Applications> Accessories> Terminal.

```
ifconfig
```

It also could be a hardware issue.  Post the results of the command below.  If you can just post your network card and if you are unsure post the whole thing.

```
lspci
```

i know that i'm connected because it says when i startup ubuntu that i'm connected to the the connection WaveLan Network and that there is fine signal, but i just can't browse the internet og use it in any way. 

What can i do ?

---

### Post by oOJINxOo on 2007-08-31
although its unlikely, check that firefox or whatever browser your using isn't configured to use a proxy.

but what ya really need to do is what wormser said, if you do and are not sure where to go from there, paste the output in here, and i'm sure someone will help.

maybe the network uses mac addresse filtering.

---

### Post by czepluch on 2007-08-31
> **oOJINxOo said:**
> although its unlikely, check that firefox or whatever browser your using isn't configured to use a proxy.

but what ya really need to do is what wormser said, if you do and are not sure where to go from there, paste the output in here, and i'm sure someone will help.

maybe the network uses mac addresse filtering.

I know that the network uses Mac-addresses

---

### Post by czepluch on 2007-09-02
bump

---

### Post by alienexplorers on 2007-09-02
Please post the output of ifconfig and lspci to this page.  You may be able to connect to the network, but that does not mean you have full use.  you could also try using another browser like opera and see if it works.  If it does you might have a profile error in firefox.

---

### Post by czepluch on 2007-09-02
> **alienexplorers said:**
> Please post the output of ifconfig and lspci to this page.  You may be able to connect to the network, but that does not mean you have full use.  you could also try using another browser like opera and see if it works.  If it does you might have a profile error in firefox.

Thanks, but I can tell you this much: The network is using mac-address(some guy on my school did so that i can use the internet in XP but didn't do it in ubuntu) and that i cant use any other browsers. 

I will post the output of ifconfig when i'm back on the school tomorrow.

---

