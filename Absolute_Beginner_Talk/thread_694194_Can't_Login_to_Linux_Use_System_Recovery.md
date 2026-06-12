---
title: "Can't Login to Linux/ Use System Recovery"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Kong on 2008-02-11
I guess i installed Linux unprepared, but that's just the least of my problems. Keep in mind I know very little about how operating systems work, etc. 

I downloaded Linux a few weeks ago, without using an install disc, so it was downloaded straight into my PC (an HP running XP). I went through the install instructions, which seemed to work fine. When I tried to login to the PC, though, I can't. I provide my username and pass, which works fine (I get the "Ubuntu comes with no warranty" message), and they ask for a third thing. What do I type here?

Also, the recovery built into my PC no longer works, and I don't have recovery discs. Would buying them be a waste?

---

### Post by nikoPSK on 2008-02-11
> **Kong said:**
> I guess i installed Linux unprepared, but that's just the least of my problems. Keep in mind I know very little about how operating systems work, etc. 

I downloaded Linux a few weeks ago, without using an install disc, so it was downloaded straight into my PC (an HP running XP). I went through the install instructions, which seemed to work fine. When I tried to login to the PC, though, I can't. I provide my username and pass, which works fine (I get the "Ubuntu comes with no warranty" message), and they ask for a third thing. What do I type here?

Also, the recovery built into my PC no longer works, and I don't have recovery discs. Would buying them be a waste?

Third thing? please describe.

---

### Post by Kong on 2008-02-11
Not sure what it is, to be honest. I'm using someone else's PC at the moment, but it shows my name, and some letters and numbers, I believe. For instance, it would be "kong@-892-137-BDY". Something similar to that. 

I apologize for not being able to explain in greater detail. =/

---

### Post by Kong on 2008-02-11
I apologize or bumping so early, I guess I'm just impatient. Can anyone help me here?

---

### Post by akiratheoni on 2008-02-11
It seems as though you're dropping into the command line. Try typing in 
```
startx
```

Then hit enter.

---

### Post by Kong on 2008-02-16
Haven't been online in a while now, but I still can't log in. I tried startx, but it wouldn't work. Now whenever I reboot my PC, a few things are marked as "Failed" rather than "OK."

---

### Post by Peter09 on 2008-02-16
You are going to have to tell us a bit more about what you are seeing. It does sound like you are at the command prompt.

What happens when you type 

startx

---

### Post by markharding557 on 2008-02-16
did you use the alternate cd ?,sounds like you have no gui installed.
try > sudo apt-get install ubuntu-desktop gdm xorg
and see what happens

---

### Post by dicecca112 on 2008-02-16
> **markharding557 said:**
> did you use the alternate cd ?,sounds like you have no gui installed.
try 
and see what happens

Or Xorg didn't configure right for his graphics card.  Help if we had the specs of the install machine, how he installed (did he burn the ISO and run it)?

---

### Post by markharding557 on 2008-02-16
> **dicecca112 said:**
> Or Xorg didn't configure right for his graphics card.  Help if we had the specs of the install machine, how he installed (did he burn the ISO and run it)?

dicecca112 may be correct there should be an error report if xorg fails to load,kong needs to supply more info

---

