---
title: "What will happen if i switch RAM chips"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-05-23
What would happen if i took 2 ram chips that equal 250mb out of a HP and switched them with 2 ram chips that equal 556mb that are an a dell? Would this be a simple no problem thing. Or could i run into some minor problems. Please tell me what each computer would say about it when i reboot and would there be any lasting affect (suchy as pressing f2 on boot on every boot? Dells are bad for that kind of thing) 
Please help i want more RAM

---

### Post by oilchangeguy on 2007-05-23
> **microsoft92sucks said:**
> What would happen if i took 2 ram chips that equal 250mb out of a HP and switched them with 2 ram chips that equal 556mb that are an a dell? Would this be a simple no problem thing. Or could i run into some minor problems. Please tell me what each computer would say about it when i reboot and would there be any lasting affect (suchy as pressing f2 on boot on every boot? Dells are bad for that kind of thing) 
Please help i want more RAM

should be no problem as long as they are the same type of ram, pc 2100, pc 2700, pc 3200, etc.

---

### Post by mdwuznik on 2007-05-23
Mixing the types is safe, if only you find a proper combination of slots (usually that means slower module in Slot0, AFAIR)

Cheers
Michal

---

### Post by raul_ on 2007-05-23
the only thing that happens if you use the wrong slots, is that your computer won't boot...been there done that. At least i never heard of anything else

---

### Post by ndefontenay on 2007-05-23
Yep.

I dont't know about the speed, but RAM is a volatile memory. It's empty after shutdown&#12289;so there's no impact when you switch them.

---

### Post by DeadlyAura on 2007-05-23
The Linux machine will most likely be fine. The only side-affect will be an unprecedented increase in speed. But that is never a bad thing. :D

However, if you are planning to put the RAM from that PC into the Dell machine, this could cause problems.

If the RAM is SDRAM and the Dell machine is running Windows, you will have to perform a reformat. If it is DDR, you will be safe, or if the Dell is running Linux you will be safe.

Also, before you perform the swap, make sure that the RAM is identical in speed. (Not in memory size). If it is not, it is likely that one of the machines will not boot because the motherboard cannot support that speed RAM. Dell PCs have motherboard designed for the system and often times will only support a small variety of RAM.

To make a long story short, check the RAM, make sure speeds are the same. Make sure it is DDR.

If that all checks out, you will be safe to perform an easy swap. If it isn't DDR, you can still swap it, but you will have to reformat the Dell machine. (Granted the Dell is running Windows).

Hope this helps.

---

### Post by jackmc on 2007-05-23
I added ram and turned my laptop on, it was detected with me doing nothing. Big difference going from 512 to 1024!

---

### Post by wmichaelb on 2007-05-23
Forgive me, but I'm puzzled; why would a change in RAM require one to reformat the hard drive? Shouldn't the BIOS simply detect the memory in the usual way at bootup, and go on from there? Is there something about the Dell BIOS that's different than the HP's or the ASUS that I have now?

Thanks in advance; just curious. 

> **DeadlyAura said:**
> The Linux machine will most likely be fine. The only side-affect will be an unprecedented increase in speed. But that is never a bad thing. :D

However, if you are planning to put the RAM from that PC into the Dell machine, this could cause problems.

If the RAM is SDRAM and the Dell machine is running Windows, you will have to perform a reformat. If it is DDR, you will be safe, or if the Dell is running Linux you will be safe.

Also, before you perform the swap, make sure that the RAM is identical in speed. (Not in memory size). If it is not, it is likely that one of the machines will not boot because the motherboard cannot support that speed RAM. Dell PCs have motherboard designed for the system and often times will only support a small variety of RAM.

To make a long story short, check the RAM, make sure speeds are the same. Make sure it is DDR.

If that all checks out, you will be safe to perform an easy swap. If it isn't DDR, you can still swap it, but you will have to reformat the Dell machine. (Granted the Dell is running Windows).

Hope this helps.

---

### Post by DeadlyAura on 2007-05-23
Its not a matter of BIOS, its a matter of SDRAM vs DDRRAM.

Windows has a tendency to store files on SDRAM after shutdown. When you remove it and replace it with another stick, the files are lost and Windows doesn't like it. You can get lucky and not have a problem at all, or you could end up like I have 3 or 4 times and have to reformat.

DDR RAM made life much easier, you can change it as you like with no side-affects.

The BIOS doesn't affect it, the RAM style does.

Linux takes more kindly to hardware changes than Windows.

---

### Post by mdwuznik on 2007-05-24
Can you post some reference ? Looks like you do big wizardry for me...

Michal

---

### Post by scheuri on 2007-05-24
> **DeadlyAura said:**
> Its not a matter of BIOS, its a matter of SDRAM vs DDRRAM.

Windows has a tendency to store files on SDRAM after shutdown. When you remove it and replace it with another stick, the files are lost and Windows doesn't like it. You can get lucky and not have a problem at all, or you could end up like I have 3 or 4 times and have to reformat.

DDR RAM made life much easier, you can change it as you like with no side-affects.

The BIOS doesn't affect it, the RAM style does.

Linux takes more kindly to hardware changes than Windows.
By all due respect...but to me (and my limited knowledge of computing) this is completely and outmost WRONG.
SDRAM and DDR-RAM are both ERASED when power is switched off. RAM is NOT about storing data over a long period of time!

Windows does NOT such thing you just wrote. If it does I promise to do my computer engineer degree again!
The only explanation would be that the RAM in the machine which you seem to have used is supplied by power even if you "shutdown" the computer or windows. Meaning that the computer draw power from your plug for keeping data in your RAM (which is....just...you know...completely nuts...for "normal" machines at least).

Sorry...had to bring that up!
cheers
scheuri

---

### Post by toasterofirony on 2007-05-24
> **DeadlyAura said:**
> Windows has a tendency to store files on SDRAM after shutdown. When you remove it and replace it with another stick.

I'd love to know where you learnt that. What with RAM not being able to do that an' all.

Issues with memory:

- Same type of stick (SDRAM, DDR, DRRII) in the slot. If you find it hard going, it probably isn't meant to go in there.

- Same speed, because everything plays happier that way

- More is, by and large, better ;)

[editus ninjatus] Oh and make sure your mobo plays nice with the particular brand of RAM you are putting in there. I learnt that one the hard way. No permanent damage, but a world of hurt to find out why I was getting weird artefacting when I tried to play NWN!

---

### Post by DeadlyAura on 2007-05-24
> **toasterofirony said:**
> I'd love to know where you learnt that. What with RAM not being able to do that an' all.

Learned from experience. I'm sure my explanation is flawed, but that is what has seemed to happen in the past. Windows just doesn't play nice with SDRAM changes. DDR swaps have always worked fin, but on the 3-4 machines I have tried to swap SDRAM in, nasty things happened.

It only happens when I move the RAM to another channel, or remove it completely. Adding RAM never affected anything, just moving ti or removing it. That is why I used the explanation that I did.

If you do happen to know the REAL explanation for why this happens, I would love to know.

---

### Post by microsoft92sucks on 2007-05-24
The Dell is running windows but how would I find out what kind of RAM its using and if it will work and what not thanks for much Help.

---

### Post by DeadlyAura on 2007-05-24
[http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php)

Download that application, unzip it, and execute it. It will scan you system and give you a complete feedback on your entire system including DIMM type, RAM frequency, capacity, etc. This will all be located under the "Memory" tab and SPD tab.

Report this info back if you don't understand it and we will gladly analyze it for you. :D

---

### Post by microsoft92sucks on 2007-05-25
my ram chips have 2 slots. And on the Dell theres room for 4 ram chips to like mine and 2 newer ones and he has the 2 newer one's so i don't think his will work on mine(srry i don't know the poper name for these ram chips.

---

### Post by DeadlyAura on 2007-05-26
> **microsoft92sucks said:**
> my ram chips have 2 slots. And on the Dell theres room for 4 ram chips to like mine and 2 newer ones and he has the 2 newer one's so i don't think his will work on mine(srry i don't know the poper name for these ram chips.

1 slotted RAM is DDR (1, 2, or 3).

2 Slotted RAM is SD

---

