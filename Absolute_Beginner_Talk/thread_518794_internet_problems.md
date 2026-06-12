---
title: "internet problems"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by sshore on 2007-08-06
i, too, am having trouble getting on the internet with my linux box.  i replaced the ethernet adapter, but that didn't help.  i have noticed that the firefox tools does not contain  "options" .  somehow i thought that if i could fool around with the options i might be able to find the problem.

as for thunderbird, i get the same problem.  

i have tried evolution but i get the same message.

i just don'w know where to turn.  i told my son i'm too old for linux but he kept pushing me.

thank you for your help.

sophia shore

---

### Post by overdrank on 2007-08-06
> **sshore said:**
> i, too, am having trouble getting on the internet with my linux box.  i replaced the ethernet adapter, but that didn't help.  i have noticed that the firefox tools does not contain  "options" .  somehow i thought that if i could fool around with the options i might be able to find the problem.

as for thunderbird, i get the same problem.  

i have tried evolution but i get the same message.

i just don'w know where to turn.  i told my son i'm too old for linux but he kept pushing me.

thank you for your help.

sophia shore

Hi and welcome, I to thought that I was to old at one time but now my son loves Ubuntu. Could you please post the output of the command 
```
lspci
```
In the terminal located under applications, accessories, terminal and maybe we can help.

---

### Post by alienexplorers on 2007-08-06
Are you using a wired or wireless ethernet card?  This can make a big difference when asking for help.

---

### Post by sshore on 2007-08-06
here is a copy of the screenshot.  also i have a wired router.

sshore@bolero:~$ lspci
0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev b5)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20)
0000:00:14.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:14.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:14.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X (rev 5c)
sshore@bolero:~$

thank you again.
sophia shore

---

