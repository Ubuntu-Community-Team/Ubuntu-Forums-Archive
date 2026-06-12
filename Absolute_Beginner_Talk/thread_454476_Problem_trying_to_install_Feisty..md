---
title: "Problem trying to install Feisty."
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-05-25
I have an HP Pavilion 753n Desktop, 2.53GHz, 1GB RAM

Currently I'm running Dapper and when I try to upgrade to Feisty, with a Live CD, the installation quits within about 3 seconds of me clicking on the 'Run or Install' line.

I have been through this process many times, using different CD's and different hard drives but all with the same result.

Today I carefully checked the BIOS and realized that Feisty changes the BIOS order.

With Dapper:-
1st  CDROM
2nd  Hard Disk
3rd  Removable

After trying Feisty:-
1st  Removable
2nd  Hard disk
3rd  CDROM

I am totally at a loss at to what to do here and would appreciate some advice.

---

### Post by Kobalt on 2007-05-25
It is very unlikely that Dapper would change the boot order in your BIOS... Anyway, if you can see the menu Start Ubuntu of the LiveCD then the problem isn't there. On some hardware you may need to start the LiveCD with 'options' in order to boot correctly. Try to press F6 at this boot screen and then add (after a space) at the end of the line ```
noapic nolapic
```Press Enter to boot. 

There are other possible options, but these a the more common ones. If it's still not working, come back here but please detail a little further your hardware specs.

---

### Post by L Campbell on 2007-05-25
> **Kobalt said:**
> It is very unlikely that Dapper would change the boot order in your BIOS... Anyway, if you can see the menu Start Ubuntu of the LiveCD then the problem isn't there. On some hardware you may need to start the LiveCD with 'options' in order to boot correctly. Try to press F6 at this boot screen and then add (after a space) at the end of the line [quote]noapic nolapic[/code]Press Enter to boot. 

There are other possible options, but these a the more common ones. If it's still not working, come back here but please detail a little further your hardware specs.

Thanks for your interest.

However mind boggling it may sound, the fact is that after my attempted boot up with Feisty, the BIOS settings have changed.  After 4 attempts the same thing happens each time.

Obviously I have to use 2 computers, in order to post here and try to get the other machine working, so please bear with me if i am slow in communicating.

Am I to enter all of this, brackets included, after the space?

[quote]noapic nolapic[/code]

---

### Post by BHelts on 2007-05-25
are you trying to install feisty to an external hard drive?

---

### Post by L Campbell on 2007-05-25
> **BHelts said:**
> are you trying to install feisty to an external hard drive?

No, I'm trying to get the Live CD to boot up.

---

### Post by ske1fr on 2007-05-25
You checked the MD5 sum of the image you downloaded before burning it to a CD?

Tried "noapic nolapic acpi=off"?  You shouldn't need any of this with such recent hardware.  It shoud have an APIC and fully working ACPI.

---

### Post by L Campbell on 2007-05-25
> **ske1fr said:**
> You checked the MD5 sum of the image you downloaded before burning it to a CD?

Tried "noapic nolapic acpi=off"?  You shouldn't need any of this with such recent hardware.  It shoud have an APIC and fully working ACPI.

Thanks.  Yup, I actually did check the CD with MD5 sum and, in addition to that, have I have tried other CD's, all of which will install Feisty on other computers but not this one.

---

### Post by L Campbell on 2007-05-25
> **ske1fr said:**
> You checked the MD5 sum of the image you downloaded before burning it to a CD?

Tried "noapic nolapic acpi=off"?  You shouldn't need any of this with such recent hardware.  It shoud have an APIC and fully working ACPI.

OK, I got back to the screen, clicked F6, 'spaced', then entered  noapic noalpic=off
and, again, the screen went black.

I checked the BIOS and, once again, they had flipped back to:- Removable, Hard Disk, CDROM.

---

### Post by Kobalt on 2007-05-26
> **L Campbell said:**
> OK, I got back to the screen, clicked F6, 'spaced', then entered  noapic noalpic=off
It's **noapic nolapic acpi=off**

---

### Post by L Campbell on 2007-05-26
> **Kobalt said:**
> It's **noapic nolapic acpi=off**

Thanks again.

I won't be able to try it till tomorrow but I will post my results.

Kind regards.

---

### Post by L Campbell on 2007-05-27
> **Kobalt said:**
> It's **noapic nolapic acpi=off**

OK, I used your suggestion, ' noapic nolapic acpi=off ' and it made a difference in that my boot order in BIOS doesn't change when I try to boot up the Feisty Live CD.  Thank you.

However, I still can't get the Feisty CD to boot up.  I have tried 2 different disks, the one I burned and a genuine Ubuntu factory disk (and they both work in other desktop machines that I have)

I burned an Edgy Live CD and it will boot up, somewhat hesitantly but it does work.

There must be something in my machine that causes this problem but I don't know enough to even think what it might be.

Is there some kind of test I could run, or lines of code I could display that might give a clue to this situation?

To reiterate, I'm using Dapper on an HP Pavilion 753n Desktop, 2.53GHz, 1GB RAM, 80GB hard drive.

---

