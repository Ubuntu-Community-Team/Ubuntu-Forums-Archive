---
title: "[SOLVED] Text Mode"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by sksurhio on 2007-08-18
**[SIZE="5"]How to run Feisty in [COLOR="DarkOrange"]text mode[/COLOR]?Like [COLOR="Yellow"]Dos [/COLOR]in windows??? i want to installi [COLOR="DarkOrange"]nvdia[/COLOR] drivers but it asks me xserver running any one can help me? i have [COLOR="Blue"]compaq evo w4000 with 2.2GH and nvidiaGeForce MX400/400[/COLOR] grafix Acelerator card but default drivers do not support acceleration any other help regarding it??[/SIZE]**

---

### Post by funpop on 2007-08-18
just log out of x in gdm

but you dont need to install the drivers from nvidia's site,

just type:

sudo aptitude install nvidia-glx
To enable the driver, run "sudo nvidia-glx-config enable".

you could also use the restricted manager

---

### Post by r4ik on 2007-08-18
Try,

[http://ubuntuforums.org/showthread.php?t=527815&page=2](http://ubuntuforums.org/showthread.php?t=527815&page=2)

---

### Post by Arthur Archnix on 2007-08-18
Woa! I could barely read your question. Maybe use edit and reformat it to normal and I'll try again.

Edit:Looks like others have given you help. But still, please reformat. Your massive font, bold and colour usage makes me (and others I would *guess*) less inclined to help. 

We want to help you for reasons unrelated to your formatting, and so changing it to make it seem more important is only annoying, at best.

---

### Post by Ek0nomik on 2007-08-18
> **Arthur Archnix said:**
> Woa! I could barely read your question. Maybe use edit and reformat it to normal and I'll try again.

Edit:Looks like others have given you help. But still, please reformat. Your massive font, bold and colour usage makes me (and others I would *guess*) less inclined to help. 

We want to help you for reasons unrelated to your formatting, and so changing it to make it seem more important is only annoying, at best.

Nobody likes teh forum police.  :p

For a GeForce MX400/400, funpop is correct and nvidia-glx should do the trick.

```
sudo apt-get install nvidia-glx
```

---

### Post by Arthur Archnix on 2007-08-18
> Nobody likes teh forum police.

Your right.

I'm sorry sksurhio. I wasn't trying to insult you or be mean

 At the same time, some ways of doing things are better than others and sksurhio needs to hear what they are. I apologize if I didn't do that tactfully enough.

---

### Post by sksurhio on 2007-08-20
Mr arthor, you dont have to apologies...

yes you are also right. so here it is...

How to run Feisty in text mode?Like Dos in windows??? i want to installi nvdia drivers but it asks me xserver running any one can help me? i have compaq evo w4000 with 2.2GH and nvidiaGeForce MX400/400 grafix Acelerator card but default drivers do not support acceleration any other help regarding it??

I also thanx to the answerers, but i forgot to tell you that I am using dialup modem and my dialup did not works on linux. i dont know why but log shows like
--> No Carrier!  Trying again.
--> Sending: ATM1L3DT13111891
--> Waiting for carrier.
ATM1L3DT13111891
CONNECT 50667
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
and did not connect the ISP. 

So forget  it ...


My actual question is that like in Red Hat the loader asks you to run in GUI or Text mode. am i able to run UBUNTU in text mode? if yes then how???:lolflag:

---

### Post by sksurhio on 2007-08-20
well guys i have tried text mode by pressing Ctrl+Alt+F1 to F6 and when i am installing nvidia drivers (downloaded from my windows XP) with command sh NVIDIA-Linux-x86-1.0-9755-pkg1.run and 
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run it gives me error for Xserver running in both GUI and text (as stated above). any help for that....

---

### Post by RomeReactor on 2007-08-20
Hi. Once you're in the command line, enter this before trying to install the drivers:
```
sudo /etc/init.d/gdm stop
```

---

