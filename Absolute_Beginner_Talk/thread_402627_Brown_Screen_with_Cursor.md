---
title: "Brown Screen with Cursor"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ligerlover123 on 2007-04-06
I'm new to ubuntu and burned the live disk to see what it's all about.  I can get the cd to boot, then I hit *start or install ubuntu*.  Then, it takes me to a black screen and says cannot enable RNG and some other stuff...then it loads to the brown screen with a cursor.  It makes a wierd noise and then the disc stops loading.   

I have a Toshiba M45 S265 with 512 MB of RAM.  I ran the disk on a friend's computer that is almost identical to mine and it worked fine.

THANKS!

---

### Post by mac.ryan on 2007-04-06
> **ligerlover123 said:**
> I ran the disk on a friend's computer that is **almost** identical to mine and it worked fine.

The keyword here is "almost" ;) I suggest you check what are the specs that differs between your two computers and post them here, so that other users can focus their attention and suggestions on those specifically.

I think it might be an issue with your video card. When your computer locks up, what does happen if you press CTRL+ALT+F2 ? Does is get to a text terminal where you can issue commands (a bit like the old ms-dos?), or... ?

Also, do you have a chance to check if you and your friend have the same bios settings? (the BIOS is the utility you can access during the very first instants after you switch on your computer...).

---

### Post by ligerlover123 on 2007-04-07
My friend has the Toshiba Satalite M35X-S163 with Phoenix BIOS version 1.90 and I have the Toshiba Satalite M45-S265 with ACPI BIOS version 1.70.  That could be the problem, but it seems like it should still work.

My video card is Mobile Intel 915GM/GMS,910GML Express CHipset Family.

When I press CTRL+ALT+F2 it takes me to the text terminal.  The last line says: ubuntu kernel: [17179576.016000] Disabling IRQ #10.

Thanks for your help!

---

### Post by mac.ryan on 2007-04-07
The fact you can get to a terminal window (CTRL-ALT-F2) means that your system works fine in nongraphical environment. (This at least allows to exclude a given number of other hypothesis).

To me (but I am not an expert) it looks like a bios problem. Googleing around it looks like it might be a problem in the bios assignment of IRQs. Indeed IRQ #10 could be shared (and thus generating conflicts) between the intel video chipset and sound devices, for example.

I am not at all an expert in this field of problems but I wold try the following steps, seeing if the CD will boot after each of them:[LIST=1]
[*]resetting bios configuration to the default settings (you might wish to copy your present settings, just in case something goes wrong and you need to reverse the change)
[*]upgrading the bios if there is a chance to (visit your vendor's website)
[*]at the boot menu, press F6 (other boot options). Remove "splash" and try: irqpoll
[*]try booting in safe graphic mode **following [this how-to]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")** (otherwise it won't work for sure).[/LIST]Anyhow... maybe somebody else will be able to perform a more accurate analysis and help you on the basis of a deeper knowledge than mine...

Let us know if you can work this out! :)

---

### Post by ligerlover123 on 2007-04-09
FINALLY!!  I got it loaded by changing splash to IRQPOLL....what exactly does this do?  Thank you for the tips

---

### Post by mac.ryan on 2007-04-10
> **ligerlover123 said:**
> FINALLY!!  I got it loaded by changing splash to IRQPOLL....what exactly does this do?  Thank you for the tips

Glad that you managed to work this around.

[B]Please keep in mind I am not an expert and the below explanation might be very approximative and _even wrong_ in some of it's parts.
[/B] 
irqpoll, is a parameter you can pass to the linux kernel while booting up.

_In my understanding_, irqpoll takes on the linux kernel the job of checking for IRQs (Interrupt requests, basically a signal that is sent out by components of your computer asking for attention), rather than leaving this task to the BIOS.

As IRQs can be shared between different pieces of hardware, at times - if the requests are not managed consistently - conflicts may arise between peripherals.

In your case, it seems like the BIOS might not manage correctly what Linux Kernel does. This is why an upgrade of your bios _might_ solve your problems as well.

Irqpoll has a small effect on your machine performance (demanding your linux kernel to do some additional operations) but this is normally not perceivable on a human scale.

**If any other more competent user would like to correct/complete the information above, I would be only glad to improve my own knowledge of the issue... so, don't be shy! ;)**

---

