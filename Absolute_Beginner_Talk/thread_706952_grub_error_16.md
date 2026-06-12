---
title: "grub error 16"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by musky on 2008-02-24
G'day,

Tried googling so understand it a bit & spent many hrs on this, but dunno what to do form here.
Got some boots & sometimes didn't but stuck now on error 16. 
Works fine on another HD with feisty, boots normal.
Maybe I could copy paste the menu list from the one that boots to the one that doesn't?
pls find attached menu list (think i did it right).
I could copy paste it here but I thought it'd be loong..
Works & boots fine with another linux live cd.
thx

---

### Post by spiderbatdad on 2008-02-24
16 : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

---

### Post by bazzawill on 2008-02-24
I think I've had this error with sata and pata drives experement by changing the root(hd0,0) to (hd1,0) worked for me

---

### Post by musky on 2008-02-24
> **bazzawill said:**
> I think I've had this error with sata and pata drives experement by changing the root(hd0,0) to (hd1,0) worked for me

I could try this.:) I see 5 entries for root(hd0,0) & I'll assume that all 5 have to be changed to (hd1,0)

---

### Post by musky on 2008-02-25
Hmm..seems to be read only, so far no luck in making the changes. Maybe there's a boot option from the cd that I could try?
Should mention that I messed about with supergrub to try to sort it out & dunno if the menu list is still ok. 
I'll be looking at the one that boots good.

---

### Post by bazzawill on 2008-02-27
you need sudo access to edit the menu.lst to do that you can use run application by pressing alt+F2 then type gksudo gedit /boot/grub/menu.lst another option instead of editing the menu.lst right away when the grub menu loads highlight windows and press e to edit the entry and then e again on the root(hd0,0) and change that to (hd1,0) press enter and then b to boot, that way you don't have to permanently change your menu without knowing it works.

---

