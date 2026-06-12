---
title: "Interesting, Yet Frustrating Problem"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by tiC_t0k on 2007-03-05
hi,

let me start off with my computer specs:

AMD Athalon 64x2 Duel Core Proccssor 3800+
1.5GB of ram
MSI GeForce 6800gs 256mb

ok,
I recently downloaded ubuntu (6.10 Edgy version) so i downloaded it from ubuntu.com and burned the image to a cd as described. i change the resolution so it will allow me to boot, i change it to 1024x768x32. so i boot up and i can see there is some icons in the lower right hand corner missing and my mouse pointer is not visible. When i mouse over icons and such it lights up and when i click it responds but i can not see my pointer. i tried both the AMD64 version and the I386 version of 6.10 and both normal boot and graphics safe mode. please help!

tiC_t0k

---

### Post by lamalex on 2007-03-05
have you installed nvidia drivers or are you running off of the included ones? try installing nvidia drivers.

---

### Post by tiC_t0k on 2007-03-05
> **Iamalex said:**
> have you installed nvidia drivers or are you running off of the included ones? try installing nvidia drivers.

i have the latest drivers from nvidia

---

### Post by konungursvia on 2007-03-05
You also need to edit /etc/X11/xorg.conf but I don't know the settings you need to put, maybe if you search the forums.

---

### Post by tiC_t0k on 2007-03-05
if anybody knows please post what to do here. or if u have any other ideas please post

---

### Post by LookTJ on 2007-03-05
don't put 1024x768x32 just put 1024x768. make sure depth is 24 bit color.

---

### Post by tiC_t0k on 2007-03-05
> **Taylor said:**
> don't put 1024x768x32 just put 1024x768. make sure depth is 24 bit color.

when i hit F4 to get the VGA to change the resolution, there is only 1024x768x32 or 
1024x768x12, so i picked 32 because when i choose 12 it wont boot up.

---

### Post by lamalex on 2007-03-05
i think he means in xorg.conf. can you post that here as well?

---

### Post by tiC_t0k on 2007-03-05
i right click on the cd in the drive and click explore, i search within the disk and it says there isnt a file called xorg

---

### Post by tiC_t0k on 2007-03-05
so does anybody know what is going on?

if you have an idea message me here or:

aim: MrT1ki
msn: [email]horralltiki@hotmail.com[/email]
xfire: torridtiki

---

### Post by iGadget on 2007-03-23
I wish someone knew because I have the same problem.

---

### Post by Rizado on 2007-03-23
Start a terminal, run: ```
cat /etc/X11/xorg.conf > postThisConfig
```

In your home directory you will now find a text file called postThisConfig. Post it's content here. Config files aren't located on the cd but on your computer.

---

