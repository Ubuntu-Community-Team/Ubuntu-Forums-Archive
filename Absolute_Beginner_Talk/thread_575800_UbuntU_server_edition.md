---
title: "UbuntU server edition"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Vendeta on 2007-10-14
im new to linux servers but i want to run a ubuntu server on my old compaq but when i put the cd in the computor goes to a black screen with a under score flashing in the top left corner and dosnt do anything i tryed a normal ubuntu disc to see if it was the disc but the same thing happend i set the bios to Cdrom, a , c (is that right)

anyhelp would be aporeciated

---

### Post by Pumalite on 2007-10-14
Follow this guide:[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Burn at 4x
Make sure you do md5sum on iso before burn

---

### Post by Vendeta on 2007-10-14
> **Pumalite said:**
> Follow this guide:[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Burn at 4x
Make sure you do md5sum on iso before burn

no i know how to burn a iso its burned and done properly i think its somthing wrong with my bios setup but i dont know how to fine tune it...

---

### Post by Pumalite on 2007-10-14
In BIOS, go to BOOT>set CD drive to 1st in Boot order.

---

### Post by Vendeta on 2007-10-14
> **Pumalite said:**
> In BIOS, go to BOOT>set CD drive to 1st in Boot order.

k i did taht it still just goes to that blinking underscore

---

### Post by Frak on 2007-10-14
You did burn it as an image and not as a file correct?

---

### Post by Pumalite on 2007-10-14
Clean the lens in your burner too; just in case.

---

### Post by mlentink on 2007-10-14
> **Vendeta said:**
> i want to run a ubuntu server on my old compaq

Couple of questions.
- What version of Ubuntu are you trying to install? Desktop or server?
- Could you tell us a bit more about the specs of that 'old' Compaq you're trying to install on?

---

### Post by Vendeta on 2007-10-14
> **mlentink said:**
> Couple of questions.
- What version of Ubuntu are you trying to install? Desktop or server?
- Could you tell us a bit more about the specs of that 'old' Compaq you're trying to install on?

umm i think i figured out the problem i booted into the windows installed on it and then it didint detect any of the 2 cd drives in the computor and i dont know how to make it detect them...

---

### Post by llamakc on 2007-10-14
Either set BIOS to autodetect or go in and discover them in BIOS.

---

### Post by Vendeta on 2007-10-14
> **llamakc said:**
> Either set BIOS to autodetect or go in and discover them in BIOS.

how do i do that? im a bit of a noob sorry....

---

### Post by Frak on 2007-10-14
> **Vendeta said:**
> how do i do that? im a bit of a noob sorry....
When you boot, you should see your BIOS screen, and it should say something like "Press (some key) to enter setup"

Just press that key, goto Boot and set CD drive as first boot order. Also, make sure your CD drives are enabled as working, in a tab such as Hardware or Peripherials.

---

### Post by Vendeta on 2007-10-14
> **Frak said:**
> When you boot, you should see your BIOS screen, and it should say something like "Press (some key) to enter setup"

Just press that key, goto Boot and set CD drive as first boot order. Also, make sure your CD drives are enabled as working, in a tab such as Hardware or Peripherials.

in the intergraded peripherials tab it dosnt show any cd drives... how do i make it show them?

---

