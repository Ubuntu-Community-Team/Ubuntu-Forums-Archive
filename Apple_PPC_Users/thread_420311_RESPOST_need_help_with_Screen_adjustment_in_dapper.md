---
title: "RESPOST need help with Screen adjustment in dapper"
date: 2007-04-23
forum: Apple PPC Users
---

### Post by bigred3373 on 2007-04-23
i have been trying to install dapper on my old clamshell 366mhz fire wire 10gb 350mb ram it installs and goes through the normal process then goes to the black screen. How do i change the preferences for the screen the refresh and verts:confused: :mad:   
ANYONE WITH AN IDEA here are specs  I have installed dapper on my laptop clamshell indigo 366 mhz 10gb 350 mb when dapper loads i get the ding to tell me i am at the desktop but montior stays black  any body have this problem its s a tough notebook and runs well considering its 800x600 screen . It is an ATI, RageM3 vram 8mb ATI (0x1002) 32 bit color thanks also when running live CD it won't give me a screen once it all loaded black

---

### Post by ewout klimbie on 2007-04-24
have you tried to pass the following parameter when ubuntu asks which kernel to load?
```
video=800*600@60-32
```

---

### Post by bigred3373 on 2007-04-24
> **ewout klimbie said:**
> have you tried to pass the following parameter when ubuntu asks which kernel to load?
```
video=800*600@60-32
``` no it just go through to the start up screen and dings and stays black i cannot input anything:( is there a menu option like the ctrl alt f1 do i have to use that then try this code?????

---

### Post by ewout klimbie on 2007-04-24
I dual boot Ubuntu and Tiger, on boot yaboot ask me if i want to boot linux, mac os x, or cdrom. If I choose Linux i get a screen similar to the livecd in that i can choose a kernel (linux or old) and am able to pass a parameter (like the one mentioned before).

You can configure yaboot differently yourself and add boot parameters, [this]("http://www.debian.org/ports/powerpc/inst/yaboot-howto/") is where google led me.

---

### Post by bigred3373 on 2007-04-24
> **ewout klimbie said:**
> I dual boot Ubuntu and Tiger, on boot yaboot ask me if i want to boot linux, mac os x, or cdrom. If I choose Linux i get a screen similar to the livecd in that i can choose a kernel (linux or old) and am able to pass a parameter (like the one mentioned before).

You can configure yaboot differently yourself and add boot parameters, [this]("http://www.debian.org/ports/powerpc/inst/yaboot-howto/") is where google led me.

this is forgein to me  i am still new to the Ubuntu family i am running Tiger and Ubuntu and dual boot through rEfFit or whatever it is on my IMAC 17 inch however i have an older model ibook and it wont give me a screen i know i just need the vert and refresh for the montior and that will fix it i cant find those though you know of them?

---

### Post by ewout klimbie on 2007-04-24
sorry haven't got a clue, did you mail Apple?

---

### Post by bigred3373 on 2007-04-25
no and i looked all over for these specs  hmmmm thanks anyway

---

