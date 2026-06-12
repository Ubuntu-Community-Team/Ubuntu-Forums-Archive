---
title: "Hp6109 and ubuntu sound issues"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by PatrickMoore on 2008-03-07
Ok i just recieved my shiny new ubuntu discs in the mail and i am getting ready to install. when i run the live disc. at first i couldnt log on  due to the fact that when i ran the startup from the disc it would run through all the hardware then the screen would go blank and then freeze. i found a work around for that i've disabled the acpi at startup. however now when i log on the only sound i'm getting is this annoying repetitive  clanking noise from my speakers. i belive that it is a sound loop of the log on sound that is sticking on one note. please help me resolve this i am really excited to use ubuntu.

my specs.
HP DV6109om 
Amd Turion 64 processor
1gb ram
Nvidea graphics card

also should i run the 64 bit disc or the normal.i read somewhere that i should use the normal disc as it is more stable... idk let me know whats up

---

### Post by LuisGMarine on 2008-03-08
First we need to find out what kind of video card you have.  Run this command in a terminal window 

Open up** Applications > Accessories > Terminal **:

and type in this command:

```
sudo lshw -C multimedia
```

paste the output of it here.

---

### Post by PatrickMoore on 2008-03-11
sorry i just got on now while i was at work. i have a nvidia GeForce Go 6150 i believe.

---

