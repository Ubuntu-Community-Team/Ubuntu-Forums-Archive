---
title: "im a newbie attempting first install, help!?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by modulistic_terror on 2007-01-31
when im trying to install ubuntu i start "run or install ubuntu" after this the screen flickers for a secind and then flashes the warning "4294667 296000 acpi- unable to locate rsdp" and then the computer just stops when the screen says loading essential drivers.

any help would be greatly appreciated.

thanks in advance

---

### Post by meng on 2007-01-31
Try with the boot options:
noacpi noapic nolapic

And please tell us about your system specs.

---

### Post by modulistic_terror on 2007-01-31
its an old machine:
intel pentium 3 coppermine 800 mhz
gigabyte technology 6vmm motherboard
160 mb memory

---

### Post by meng on 2007-01-31
I would say you're better off installing from the Alternate CD, and using Xubuntu (Xfce) rather than Ubuntu (GNOME), because of your low RAM.

---

### Post by modulistic_terror on 2007-01-31
is there a big difference between the two distros? im kinda comfortable on ubuntu from using it occasionally at a friends house. wondering if theres another wee learning curve.

---

### Post by meng on 2007-01-31
Well you could run GNOME but it would be a tad slow on your system I think. If you're unsure about the transition, then by all means stick with what you're familiar with.

---

### Post by SinxarKnights on 2007-01-31
when you boot from CD. select the menu item that says boot in safe graphics mode. Then press F6 and type ```
acpi=off
``` then press enter. When you press F6 dont delete anything that is there just add it to the end. See if that will help.

---

### Post by modulistic_terror on 2007-01-31
is there any way i can just install straight from the disc without entering the live cd?

---

### Post by jimrz on 2007-01-31
> **modulistic_terror said:**
> is there any way i can just install straight from the disc without entering the live cd?

not on the "dektop" version, but you could download the "alternate" cd which does basically that. it uses a fairly simple and straight forward text based installer and seems to be much better suited for older systems (especially those with low RAM) than the "live" cd's graphical install.

I, too, would recommend Xubuntu for that system. Xfce is kind of similar to Gnome so, while there will be a wee bit of learning curve, it should not be that difficult a transition. I have on old laptop with a PIII 500 Ghz and 384 Mb Ram that is a bit sluggish using Gnome but rips right along using Xfce.

---

### Post by modulistic_terror on 2007-02-02
ok, so i got more ram for my pc and now the live cd works perfectly and very quickly compared to xp. i get stuck on the install at step 5 it just seems to stop while searching for my hard drive, i have a maxtor 20gb its a brand new hard drive and hasnt been formatted yet, will i need to format the hard drive and if so what kind of format?

does anybody know what could be doing this? because its driving me nuts.
please help, pretty please with sugar on top :P

---

### Post by modulistic_terror on 2007-02-02
its still not working. when i tried another hdd "an old slave" i tried to hook it up and got the following warnings

417.441022
420.396993
426.973375
446.050319
and the number keeps on getting higher is it went, i got annoyed aftr 45 minutes of numbers.

all followed by the line "buffer i/o error on device dm-0, logical block.

any help would be appreciated, im having second thoughts about linux.

---

### Post by benson444 on 2007-02-02
I'd agree with what a couple of other guys have said. If you can, get the alternate install iso. I've only installed from a desktop disk once and I didn't have any problems but it seems a lot of people do. And, I believe, it's usually at the formatting or partitioning or something to do with the HD stage.

---

### Post by Ben Sprinkle on 2007-02-02
Try the install one more time.

---

### Post by xpod on 2007-02-02
Welcome to the forums modulistic_terror:) 

Always good to see a fellow jock.:) 
Even with you extra ram you might still need an altenate cd m8.I i had very similar issues on this pc when i first installed ubuntu last year.It would run the live cd fine but stick on stage 5 of the install,although safe graphics mode did work for me.

The alternate cd should hopefully solve your problems but xubuntu may well be your best bet as already mentioned.

Good luck regardless.

An Arbroath smokie myself btw:)

---

