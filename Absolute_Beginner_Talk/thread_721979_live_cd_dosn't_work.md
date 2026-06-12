---
title: "live cd dosn't work"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-03-11
when i boot from the cd the initial screen appears normally with the option to start or install ubutu but when i click enter it takes few minutes then nothing!! just  freaky blank colorful screen, i reboot and checked the cd for defects but there wasn't any so, what should i do???

---

### Post by angel_zone on 2008-03-11
hey guys any body can help please?? i searched the forum and it may be screen resloution issue but i really did not get it

---

### Post by uberlube on 2008-03-11
You may need to input the vga into the boot process. Try pressing F6 while 'start or install ubuntu' is highlighted and then delete 'quiet splash' and add 'vga=791' and press enter.

---

### Post by angel_zone on 2008-03-11
o.k i'll try this now thanx for replay

---

### Post by angel_zone on 2008-03-12
> **uberlube said:**
> You may need to input the vga into the boot process. Try pressing F6 while 'start or install ubuntu' is highlighted and then delete 'quiet splash' and add 'vga=791' and press enter.

i tried this but i did not work:( the booting screen appears normally it takes few minutes then this blank screen with colorful lines appears instead of the desktop.any other ideas:confused:

---

### Post by uberlube on 2008-03-12
You may find some useful info in here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sandysandy on 2008-03-12
what r ur system specs. u may consider trying alternate CD for older systems.

regards

---

### Post by angel_zone on 2008-03-12
> **uberlube said:**
> You may find some useful info in here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

i'm afraid it didn't help very much :) as u just said vga=xxx nothing more. i didn't install ubuntu i just wanted to try it for the first time

---

### Post by uberlube on 2008-03-12
This is a good point. If you actually want to install Ubuntu and not just browse the LiveCD do try out the alternate install cd's. They worked for me on a few finicky systems.

---

### Post by angel_zone on 2008-03-12
> **uberlube said:**
> This is a good point. If you actually want to install Ubuntu and not just browse the LiveCD do try out the alternate install cd's. They worked for me on a few finicky systems.

i really want to but what if i installed it and the same problem persisted? what can i do then

---

### Post by sandysandy on 2008-03-12
u can consider trying live Cd of other distros. would recommend puppy linux and damm small linux. that way u can make sure that ur computer supports linux. these two distros are ideal for older machines and are not resource hungry.

regards

---

### Post by angel_zone on 2008-03-12
> **sandysandy said:**
> u can consider trying live Cd of other distros. would recommend puppy linux and damm small linux. that way u can make sure that ur computer supports linux. these two distros are ideal for older machines and are not resource hungry.

regards

i don'n know very much about computers species but i just bought it several months ago, it's not old machine

---

### Post by Fred_E _krugar on 2008-03-12
I did have those problems with Gutsy also what you will have to do is Boot In Low Graphics mode.

Should work for ya. It is like the second or third choice on the boot screen.

---

### Post by angel_zone on 2008-03-12
> **Fred_E _krugar said:**
> I did have those problems with Gutsy also what you will have to do is Boot In Low Graphics mode.

Should work for ya. It is like the second or third choice on the boot screen.

hi,i tried ur advice and it works this time:lolflag: i chose to boot in low graphics mode then entered vga=791 but fonts and icons were really small so can any body help me to pick proper usplash:confused:

---

### Post by Fred_E _krugar on 2008-03-12
well the bad part about this whole thing is you cant fix these problems till after you install Ubuntu to a harddrive.

Meaning install the graphics driver. :/ :(    Another thing you can try is just chose the low graphics mod and dont mess with the VGA part.

---

### Post by angel_zone on 2008-03-12
> **Fred_E _krugar said:**
> well the bad part about this whole thing is you cant fix these problems till after you install Ubuntu to a harddrive.

.

well, i think i.m still afraid of that part..i had a lot of painful accidents with windows made me re formated my hard drive more than once ally my data were gone:(

---

### Post by Fred_E _krugar on 2008-03-12
Just try booting again in safe graphics mod and dont mess with the VGA part.

---

### Post by jan quark on 2008-03-12
have a look at this guide for dual boot:

[LIST]
[*][http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)
[/LIST]

if you decide to install ubuntu, make a backup of you windows files

---

