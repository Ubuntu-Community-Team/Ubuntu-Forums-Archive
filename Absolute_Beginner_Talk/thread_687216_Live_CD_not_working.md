---
title: "Live CD not working"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Shaun440 on 2008-02-04
I am completely new to linux, am just up to installing it. I downloaded the .iso, burned it to a DVD, restarted my computer and boot from the CD. The screen then comes up where i select "start or install", The loading screen comes up and finishes loading, then it gets to the next command line looking screen and stops. Its not frozen as i can type at this point, but nothing happens.

I have looked in forums and websites but i cant find any problem even similar to this one. Could someone please help?

Cheers
Shaun

---

### Post by spiderbatdad on 2008-02-04
try this at the install options screen ( I feel like a broken record) Hit F6. Now you will see a kernel line with a cursor. Delete back to and including "ro --quiet splash" and add "noapic nolapic vga=771"
Or hit F1 for more options and F6 again for examples. Good luck. please report back.

---

### Post by xpod on 2008-02-04
How about "Safe graphics mode" at Start Up on the live cd,unless the above post covers that or even an alternate cd might be what you want.

Good luck either way.

---

### Post by indytim on 2008-02-04
Also, may want to exercise the "Check CD" option BEFORE actually trying to boot the ops.

IndyTim

---

### Post by xpod on 2008-02-04
> Also, may want to exercise the "Check CD" option BEFORE actually trying to boot the ops.


I must have downloaded and burnt about 50-100 Linux cd`s in my 18 months so far.....Live ones and the Alternate ones but never once have i ever had a problem in that department.
MD5 sums........?????...what are those:)

Either way though,it is always advisable to burn at the slowest speeds possible.

---

### Post by TeaSwigger on 2008-02-04
Hello Shaun and welcome. It definitely can take persistence to figure things out, but hang in there, feel free to ask and re-ask any questions, and you will. :)

What is the computer you're trying to install this on please?

---

### Post by Shaun440 on 2008-02-04
> **TeaSwigger said:**
> What is the computer you're trying to install this on please?

Im using a desktop PC i built myself. Its using a gigabye motherboard if that is of any help. 

I tried what you suggest spiderbatdad, and it didnt work. It just added a whole lot more lines at the command line stage i got to last time but froze once it got to the same line. The line reads:

"running local boot scripts (/etc/rc.local)"

just nothing after that. This is the same line it always gets to before stopping.

Also i used MD5sum and the MD5 check sums are the same

---

### Post by xpod on 2008-02-04
My lads box is currently a Gigabyte board too...GA-7VKMLS if i recall correctly.

Did you try "Safe Graphics mode" at Startup??
What GFX card do you have out of curiosity and how much RAM does your PC have???

As previously suggested though i would consider downloading an "Alternate CD"  although you wont get no Live environment to try before you buy.......so to speak.

It`s just an installer but it can save many a headache.

---

### Post by Shaun440 on 2008-02-04
ok ill try safe graphics mode and if that fails, i'll just install with the "alternate CD"

thanx for all your help. Would have been good to use the live feature first though

---

### Post by candtalan on 2008-02-04
> **indytim said:**
> Also, may want to exercise the "Check CD" option BEFORE actually trying to boot the ops. IndyTim
I also think this is useful, and in this situation is probably important.

I have a 52x cd burner which is  a few years old. When burning audio stuff I  get no problem. However when burning an iso image, when perfection is important, I soon found that as time went on, I had to burn slower. At first a high speed gave no errors. After some use I found md5 errors, but then reducing to 24x solved it, producing no errors again. This was ok for a long time. Last year I burned a lot of iso's for an event (300) so the drive laser might have aged a bit. Now I find I get a few md5 errors if I continue to use 24x, so I have had to reduce burning speed  down to 16x, and again I can get perfect burning with no md5 errors indicated. These errors are not for every burn, just sometimes. There are no obvious burning errors, the drive thinks it is good!
This is an example of what one might expect as a (domestic grade) CD drive ages, they are not expensive. Audio CD burning would probably not show any problem symptoms, not sure why. But to get a good iso burn, more validity is required.

The boot menu 'Check this CD' is very useful because it checks both the download accuracy, the burn accuracy and also the ability of the target CD drive to read it - everything together. 

It is well worth doing if there is any doubt!

hth

---

