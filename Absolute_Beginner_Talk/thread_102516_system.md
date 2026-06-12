---
title: "system"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-12
i think there is somthing rong with my liux ubuntu because every time i go into system>administration>synaptic and click nothing happens and the only thing that works is clicking on the right of mouse:confused:

---

### Post by earobinson on 2005-12-12
Im not sure i understand what "clicking on the right of mouse" means.

try ```
sudo synaptic
``` in the terminla let us know how it goes. also try ```
gksudo synaptic
``` and let us know what happens. (the second command is the same as clicking the synaptic icon)

---

### Post by richard willacy on 2005-12-12
i have been to this terminal and done what you say i have printed gksudo 
synaptice but no look and every time i go to this synaptic nothing works any help would be good because if been doing this all day, and have i gone to the right part in the ubuntu to put this what you say and nothings working:confused:

---

### Post by earobinson on 2005-12-12
what about sudo?
did you change your root password or make a new user?

try if you made a root account.
```
su
<password>
synaptic
```

---

### Post by TeeAhr1 on 2005-12-12
I think he means (correct me if I'm wrong, Richard) that the left click does nothing, but the right click brings up the context menu.

Is this only with Synaptic, or are you having the same issue with all your icons?

---

### Post by earobinson on 2005-12-12
[QUOTE=TeeAhr1]I think he means (correct me if I'm wrong, Richard) that the left click does nothing, but the right click brings up the context menu.

Is this only with Synaptic, or are you having the same issue with all your icons?[/QUOTE]
If that was the case gksudo synaptic should have worked no?
The second question is a very good one.

---

### Post by richard willacy on 2005-12-12
teeahr1 your dead right it does not matter what i click on nothing works and if i go into somthing i click onto it and nothing works but if you click to the right then some stuff comes up but nothing works

---

### Post by richard willacy on 2005-12-12
what do you mean root :confused:how do you make new account and password

---

### Post by earobinson on 2005-12-12
[QUOTE=richard willacy]what do you mean root :confused:how do you make new account and password[/QUOTE]
NM Some users mess with there settings and this is what breaks it, I assume you did not.

Can you conferm/deny if sudo synaptic worked or not?

---

### Post by richard willacy on 2005-12-12
no it did not and i have done nothing rong,i have tried all sorts of things like clicking onto diverent sections but nothing seems to work

---

### Post by richard willacy on 2005-12-12
i dont realy know what to do about this problem but there seems to be somthing a miss when i put cd into the system,maybe somthing did not download and thats why its not working but the only thing i have been doing is clicking onto things to see what happens thats all i have done and you talk about this sudo but whats sudo and where is it:confused:

---

### Post by earobinson on 2005-12-12
open up a terminal and type sudo synaptic

---

### Post by richard willacy on 2005-12-12
the first thing i do is get ubuntu to work and i get this caution alerts and this message comes at the side of this caution and all it says is could not look up internet address for ubuntu breezy,this will prevent gnome from operating correctly,it may be possable to crrect the problem by adding ubuntu breezy to the file/ect/host,

and i did go into the terminal and typed sudo and this is what it said,sudounable to lockupubuntu breezy via gethostby name () and i tried to do it in every where i went into but nothing worked:confused:

---

### Post by earobinson on 2005-12-12
hum I will have to look a bit deeper into this, I have no idea what is happening.

---

### Post by qiemem on 2005-12-12
richard, is your computer connected to the internet? I mean the one with ubuntu on it...
Are you using these forums with a different computer?

---

### Post by earobinson on 2005-12-12
even if it was not that should not stop sudo from running, nor synaptic?

---

