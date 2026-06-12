---
title: "If I add more memory, Ubuntu refuses to load up"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-07-12
My pc has 2 x 256Mb RAM chips. I installed another 512Mb (1 x 512Mb) and Ubuntu just wuldn't load. Absolutely nothing on the screen - totally dead, although the machine itself powered up. If I removed this 512Mb memory, all was fine. But it used to be fine when I had WIndows installed - I had 1Gb and no issues. So is there something I should know about why Ubuntu won't handle this extra RAM? (Prior to installing UBuntu, I removed the 512Mb RAM from the machine....)

---

### Post by jazzmuzik on 2006-07-12
Take out the 2 256's and only try the 512. If that works then the 512 bank is most likely good and it may be that are enough differences between the two types of chips that they are incompatible. If so, try and match the chip specs, (speed etc).

---

### Post by khado on 2006-07-12
well i have 1.5GB on my pc ( 1gb stick, 1 512mb stick )
ive had no problems wht so ever, 
are u sure the ram is defintly not faulty 
( have u tried booting from the cd ) ?

---

### Post by Tom Brokaw on 2006-07-12
memtest86 is a free, dos-based program that will put your memory through several rigorous tests.  I've used it a couple of times to eliminate bad sticks.

---

### Post by rejser on 2006-07-12
do you get grub? or has it halted before that? it will sound as if the computer works allright even if it does not like that kind och memory (different sizes). Do you have any means on communication on your motherboard (most these days have leds telling in one way or another if everything is alright.
If you get grub do you stil have memtest in the menu (it is there by default), run it, but it should not create this problem, only thing that can be is if you run the i386 kernel that it only recognizes 786 mb of ram for some reason

---

### Post by BlackMambo on 2006-07-12
> **rejser said:**
> do you get grub? or has it halted before that? 
Absolutely nothing. The monitor did not even start!!

---

### Post by hotstovejer on 2006-07-12
Does your computer make any beeping noises when it boots? If the monitor isn't even turning on, that tells me that there's some RAM that doesn't like to play together.

---

### Post by sharperguy on 2006-07-12
it cannot be ubuntus fault then at-least, since this is a pre-operating system problem, so more likely a hardware issue

---

### Post by Tom Brokaw on 2006-07-12
Did you doublecheck to make sure it's seated properly?  I've made that mistake a few times.

---

### Post by ubuntu-geek on 2006-07-12
Sounds like bad memory to me..

---

### Post by jimmygoon on 2006-07-12
Just put your install disk in and run the "check memory" app

---

