---
title: "ubuntut 7.04  is not able to connect to the internet"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by akash238 on 2007-12-28
ubuntu is recognizing my router that i have setup but there are no bars 
it says 0% while my router is sitting right on top of my computer
cant i just connect through my dsl modem that is connected to my computer
im on windows vista right now and the internet is working just fine
if this helps i used the wubi istaller to install ubuntu

---

### Post by mikewhatever on 2007-12-28
Yes, you can. [https://help.ubuntu.com/7.10/internet/C/adsl.html](https://help.ubuntu.com/7.10/internet/C/adsl.html)

---

### Post by TheWizzard on 2007-12-28
can you ping your router?
can you ping an IP-address? 

please give us more information.

---

### Post by akash238 on 2007-12-29
what is pinging your router

---

### Post by RomeReactor on 2007-12-29
Hi. Pinging is a way to see if you can reach a certain destination--in this case your router. If you know the address you enter in Firefox to reach your router you can use it with ping; from the terminal (Applications->Accessories->Terminal):
```
ping -c3 ADDRESS
```
the **-c3** option is to only ping three times. In my case, to go into the router I enter 192.168.1.1 in Firefox, so to "ping" the router I would do:
```
ping -c3 192.168.1.1
```
If it tells you that "All packets dropped", then you have problems reaching your router.

---

### Post by Furat on 2007-12-29
> **RomeReactor said:**
> Hi. Pinging is a way to see if you can reach a certain destination--in this case your router. If you know the address you enter in Firefox to reach your router you can use it with ping; from the terminal (Applications->Accessories->Terminal):
```
ping -c3 ADDRESS
```
the **-c3** option is to only ping three times. In my case, to go into the router I enter 192.168.1.1 in Firefox, so to "ping" the router I would do:
```
ping -c3 192.168.1.1
```
If it tells you that "All packets dropped", then you have problems reaching your router.
1- check if you can get an IP from the router from the terminal

---

### Post by Furat on 2007-12-29
First u have to check if u have an IP from the terminal write 
```
ifconfig
```

---

### Post by TheWizzard on 2007-12-30
> **akash238 said:**
> what is pinging your router


sorry i didn't explain

please follow RomeReactor's directions to ping your router. 
if that works then try: 
```
ping -c4 66.249.72.98
```
and 
```
ping -c4 www.google.com
```

you can also provide us useful information by posting the output of 
```
route -n
```

---

