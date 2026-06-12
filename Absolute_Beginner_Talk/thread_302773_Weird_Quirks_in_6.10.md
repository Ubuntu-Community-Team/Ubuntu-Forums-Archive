---
title: "Weird Quirks in 6.10"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Wandering Cloud on 2006-11-19
Hi
I just upgraded to 6.10

From a hardware perspective, it went fine. Everything works except the modem, but I never use that anyway.

However, I noticed a few odd things once I had upgraded.

1. the number of workspaces(the boxes in the lower right hand corner) had decreased from 4 to 2. Is that intentional?

2. The fonts, which where bearable in 6.06, are now absolutely hideous. 

3. the update manager no longer works. I can defiantly connect to the Internet, but for some reason, it has a little 'can't connect' icon in the top left hand corner. What the hell?

---

### Post by slimdog360 on 2006-11-19
1) right click on it --> preferences

2) system--> preferences-->font

3)would not have a clue why that is happening. Try using the command line ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Wandering Cloud on 2006-12-08
Hi
Sorry for taking so long.
Anyway, I can test out that command because I am downloading updates as I type. Oddly enough, it is still saying that there is not network connection to speak of. Also, the internet is running really slow to what it was in 6.06.

Has anyone any idea how to fix this?

---

### Post by Wandering Cloud on 2006-12-10
So does anyone know any way of fixing the fact that Ubuntu is falsely claiming that it cannot connect to the Internet, when it most defiantly can.

---

### Post by igknighted on 2006-12-10
Have you disable ipv6?  This is the only thing I can think of.

---

### Post by Tzumli_D on 2006-12-10
I also have that icon. However, it may mean that there is no network connection meaning a network of local computers, rather than the internet. 
That's what it means in the ms environment.
Denise

---

### Post by Wandering Cloud on 2006-12-18
ok, sorry for the long reply.
How would you disable ip6?

Oh, and that does look like it is the problem denise, because even though I can connect to the internet, I cannot connect to my local windows network.

Does anyone know how to fix that?

---

