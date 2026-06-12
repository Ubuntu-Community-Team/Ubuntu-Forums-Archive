---
title: "ubuntu 6.04 pavillon dv6000"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by yveslens on 2007-09-08
Hello
i va a Pavillon DV6000 AMD Turion i ve tried to install ubuntu in dual boot with Vista .  no result

I va installed ubuntu 6.04  it stoped during boot
So i ve instaled alternate 64. Installtion was correct but whe i boot , it stop
So when i boot  on recovery the 1st time it stop on  and onsetting up console font and keymap and during the following boot  on loading drivers

I ve read i should put noapic  but i dont know how to

1 question. is it the solution
2 question hw to do

Please i m new on Linux and it's not easy

Thanks for your help

---

### Post by overdrank on 2007-09-08
> **yveslens said:**
> Hello
i va a Pavillon DV6000 AMD Turion i ve tried to install ubuntu in dual boot with Vista .  no result

I va installed ubuntu 6.04  it stoped during boot
So i ve instaled alternate 64. Installtion was correct but whe i boot , it stop
So when i boot  on recovery the 1st time it stop on  and onsetting up console font and keymap and during the following boot  on loading drivers

I ve read i should put noapic  but i dont know how to

1 question. is it the solution
2 question hw to do

Please i m new on Linux and it's not easy

Thanks for your help

HI and welcome, after searching the forums it appears that command has help some and some had to add additional commands as well. You can add these commands to the kernel line
```
noapic  nolapic
```
by using the escape key when the grub is loading and and then select the kernel line and press e to edit and add those commands. Then to continue booting just press the b key. Now this will only work if ubuntu is installed.
If you need to add the commands when using the live cd then you will use the F6 key when you see the ubuntu start or install screen and then add those command just before you see the --  ad the end of the kernel line at the bottom of the screen. Hope this helps and good luck!

---

### Post by meborc on 2007-09-08
hmm... are you using 6.06 LTS or 7.04... as there is no ubuntu 6.04 :)

if you are using 6.06, then i strongly recommend switching to feisty (7.04) ... newer ubuntu - newer kernel - better HW support

---

### Post by yveslens on 2007-09-08
hello
Thanks to take time to anwer
I m on 7.04 i ve installed alternate

so i ve booted and i have edit the kernel line
i ve actually
<c------------------------ to quiet splash
what must i do

I m sorry i dont know at all linux

---

### Post by overdrank on 2007-09-08
> **yveslens said:**
> hello
Thanks to take time to anwer
I m on 7.04 i ve installed alternate

so i ve booted and i have edit the kernel line
i ve actually
<c------------------------ to quiet splash
what must i do

I m sorry i dont know at all linux

You can remove quite splash and place noapic nolapic in its place before the --

---

### Post by yveslens on 2007-09-08
hello thanks to take time  to answer me
i va replaced quite..... by  napic nolapic 
The system boot ans it stops on Running local boot scripts (/etc/rc.local
when i do Return i arruve to the login

---

### Post by overdrank on 2007-09-08
> **yveslens said:**
> hello thanks to take time  to answer me
i va replaced quite..... by  napic nolapic 
The system boot ans it stops on Running local boot scripts (/etc/rc.local
when i do Return i arruve to the login

Great glad it worked and good luck! :popcorn:

---

### Post by yveslens on 2007-09-08
Hello yes it works but how to get  graphic (interface), and i don t know how to save the line nolapic....
Thanks

---

