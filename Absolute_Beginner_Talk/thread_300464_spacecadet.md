---
title: "spacecadet"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by spacecadet on 2006-11-15
very newbe..1 cup of ubuntu..so far! very old hardware man, no coding or hacking experince.. set up of 6.10 edgy eft was without a gremlin one!! trying to 3d my vidio is becoming a pain in the thrusters. download the nividia glx using the package manager then entering the sudo line in the gnome window.then reboot and open gnome again and put in nvidia-settings here is what i get: error: NV-CONTROL extenshion not found on this display
next line: ERROR: unable to determine number of NVIDIA GPU's on':0.0.
next line: ERROR: unable to determine number of NVIDIA frame lock devices on ' :0.0. using P4 3.4G HT, Asus p4c800deluxe, 160gigwd sata no raid, old fx5500le vidio card 128meg,1.5gig memory on the main..any help will be without shashbot..many stars and garters will be burned in your honor..please keep me from going any spacer than i am..azlizird@yahoo.com

---

### Post by yurtfg89327tfg0o on 2006-11-15
Posting your /etc/X11/xorg.conf would help

---

### Post by spacecadet on 2006-11-16
thank you for the reply..may i please ask for translation to basic english..i am sorry but i am not fluent in any coding language. please bare with me!!!azlizird@yahoo.com

---

### Post by MetalMusicAddict on 2006-11-16
Please use a proper description in your thread title.

---

### Post by Redache on 2006-11-16
What he needs from you is your xorg.conf file. To open it easily open a terminal (Applications - Accessories - Terminal)
and Type this command 

```
sudo gedit /etc/X11/xorg.conf
```

Then copy it's output and paste it here.

---

### Post by seijuro on 2006-11-16
depending on how old your "old hardware" is you may need the nvidia-glx-legacy drivers rather than the new driver my older tower has an nvidia geforce2 ti which required the legacy package.

---

### Post by spacecadet on 2006-11-16
thankyou all, I shall try all your suggs, and directions. All I know(sic) I read in the funnies and kier's ubuntu begginer book!!azlizird@yahoo.com

---

