---
title: "Ubuntu live CD not going through in Acer notebook"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by durkhrod chogori on 2007-08-14
I got here my gf's laptop (Acer Aspire 3618AWLCi) and the damn thing is not letting me play with the live CD so I can get rid of Wincrap and install Ubuntu Feisty. It's one of those machines where Acer has an special system where you need to burn the OS on a disk as they don't supply with either Win's live CD or the recovery CD. The OS is XP Home edition.

What can I do to bypass Acer's system and successfully install Ubuntu.

I get a message saying that there is an error and Gnome can't continue with the installation. I know as a matter of fact that this problem is related to what I just mentioned above.

Any help is greatly appreciated.


Cheers.

---

### Post by uzerzero on 2007-08-14
If you're reaching a Gnome screen, it would be a problem with the boot process on the CD, not the laptop. Try tacking on some extra commands to the boot line (press F6 I think), a lot of laptops have ACPI issues. Delete the last two dashes at the end, and add ```
live acpi=off
``` and ```
noapic
```

That should give you some results.

---

### Post by jenson on 2007-08-14
> **durkhrod chogori said:**
> I got here my gf's laptop (Acer Aspire 3618AWLCi) and the damn thing is not letting me play with the live CD so I can get rid of Wincrap and install Ubuntu Feisty. It's one of those machines where Acer has an special system where you need to burn the OS on a disk as they don't supply with either Win's live CD or the recovery CD. The OS is XP Home edition.

What can I do to bypass Acer's system and successfully install Ubuntu.

I get a message saying that there is an error and Gnome can't continue with the installation. I know as a matter of fact that this problem is related to what I just mentioned above.

Any help is greatly appreciated.


Cheers.

Hi durkhrod,

I'm relatively new to Ubuntu too. BTW, have you checked your LiveCD that it's a working copy? Are you using the exact copy which you used to install on another machine?I'm quite concerned about spoilt CD =)

Other problems might require other experts to help you.

My younger sister-in-law does has a Acer laptop, and it has problem with graphic card when come to installing games that only require 32MB video memory, but it's an integrated card which is so crappy that even loading the CD to install will give me error and end up not bootable at all. I'm not sure whether it is due to the graphic card or not as the CD running well on my machine.

Sorry to say that I don't really like Acer system, haha..I have some bad experiences with them and that make me always stick with my Toshiba which I find it quite durable and I have an old toshiba which last me 6 years and it's still functioning well, I planned to load it with Ubuntu Feisty Fawn when I get it back from my sister-in-law (yes, she also borrowed my old Toshiba notebook).

Do tell us if you get this fixed so that I know what to look out for when I have to install something or Ubuntu in the future for Acer system ;)

Cheers!

Jenson

---

### Post by durkhrod chogori on 2007-08-14
uzerzero,

I try that tomorrow and see how it goes. I hope pressing F6 works because when I had that issue neither the mouse nor touchpad worked. I was forced to press the switch button.

Jenson, yeah, stay tuned.

Cheers.

---

### Post by durkhrod chogori on 2007-09-07
> **uzerzero said:**
> If you're reaching a Gnome screen, it would be a problem with the boot process on the CD, not the laptop. Try tacking on some extra commands to the boot line (press F6 I think), a lot of laptops have ACPI issues. Delete the last two dashes at the end, and add ```
live acpi=off
``` and ```
noapic
```

That should give you some results.

Hi, I tried that and zilch. Ended up in a screen full of codes and asking me for YES or NO to if I wanted to have some stuff checked (can't remember what it is, sorry). I clicked YES and same. Dead end road.

Any alternative ways to install Ubuntu is this box?

**Acer Aspire 3618AWLCi**

Thanks.

---

### Post by jenson on 2007-09-10
> **durkhrod chogori said:**
> Hi, I tried that and zilch. Ended up in a screen full of codes and asking me for YES or NO to if I wanted to have some stuff checked (can't remember what it is, sorry). I clicked YES and same. Dead end road.

Any alternative ways to install Ubuntu is this box?

**Acer Aspire 3618AWLCi**

Thanks.

Hi Durkrod,

I'm not sure whether I misunderstood your problem, are you saying that you are installing it? Btw, in the first place, can your LiveCD load up during your notebook boot up? Does it goes into configuration page with a lot of wordings or commands running on the screen with a lot of [OK] at the right end?

Hmm, and did you boot into the LiveCD before you actually click on the Install Ubuntu icon on the GNome desktop?

Sorry if I've asked a series of stupid questions :)

Cheers,
Jenson

---

