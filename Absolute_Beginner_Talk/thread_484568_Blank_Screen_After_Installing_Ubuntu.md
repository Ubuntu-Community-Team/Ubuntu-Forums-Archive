---
title: "Blank Screen After Installing Ubuntu"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by proplaya23 on 2007-06-25
Hi there,

I have just installed Ubuntu and after selecting Ubuntu from the GRUB loader the screen brings up Something like..."Bug : 8254 timer not connected" then it goes BLANK and my monitor light on my LCD turns Orange.

I have edited the boot line and added the noapic nolapic commands and the error message goes away leaving me after that with a Blank screen again.

Amd Athlon 64-bit 3500+
1gb RAM PC3200
200GB HDD
Asus A8AE-LE MB
Ati radeon x800 Crossfire Edition PCi-express(onboard Video disabled or not in use)
Realtek AC 97 Audio

Also before when i inserted the LiveCD ubuntu 7.04 it boots up perfect but i have to press F4 and select my video resolution from the VGA menu so it doesnt give me a blank screen. 

I think its an Video Problem ??

Also i forgot to point out that i am Tri-Booting Vista, XP, and Ubuntu

Hope this Helps Thanks
if you need more info let me know.....im a total nub to LINUX:popcorn:
but its Absolute Beginner Talk ;)

Windows Vista SUcks by the way!!

---

### Post by proplaya23 on 2007-06-26
wow looks like evryone is sleeping:(.............. ok then ill check back in the morning to see if anyone found a solution or im just a nub that doesnt know what the heck hes talking about:p

---

### Post by proplaya23 on 2007-06-26
Another day guys, GoodMorning im trying my best on my own to figure out the problem through google or my own knowledge but yet to have success so please if someone can point me in the right direction it will be enough.

---

### Post by proplaya23 on 2007-06-26
> **proplaya23 said:**
> Hi there,

I have just installed Ubuntu and after selecting Ubuntu from the GRUB loader the screen brings up Something like..."Bug : 8254 timer not connected" then it goes BLANK and my monitor light on my LCD turns Orange.

I have edited the boot line and added the noapic nolapic commands and the error message goes away leaving me after that with a Blank screen again.

Amd Athlon 64-bit 3500+
1gb RAM PC3200
200GB HDD
Asus A8AE-LE MB
Ati radeon x800 Crossfire Edition PCi-express(onboard Video disabled or not in use)
Realtek AC 97 Audio

Also before when i inserted the LiveCD ubuntu 7.04 it boots up perfect but i have to press F4 and select my video resolution from the VGA menu so it doesnt give me a blank screen. 

I think its an Video Problem ??

Also i forgot to point out that i am Tri-Booting Vista, XP, and Ubuntu

Hope this Helps Thanks
if you need more info let me know.....im a total nub to LINUX:popcorn:
but its Absolute Beginner Talk ;)

Windows Vista SUcks by the way!!

Another day guys, GoodMorning im trying my best on my own to figure out the problem through google or my own knowledge but yet to have success so please if someone can point me in the right direction it will be enough.

---

### Post by proplaya23 on 2007-06-26
i have Fixed the Problem Woot!!!:D

All i had to Do was add a line of code to the Boot Line and its Flawless.

VGA=791   ( 1024x768 )  8)


But can anyone tell me why ubuntu didnt figure this out on its own???


THX in Advance

---

