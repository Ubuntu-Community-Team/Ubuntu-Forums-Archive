---
title: "[SOLVED] Cant Select OS with Keyboard after installin unbuntu"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by SILLAT on 2008-02-22
Xp was my 1st OS then i install Ubuntu to dual boot with it. after i finish installin ubuntu at the grub screen where u chose the OS u want to use, when ever i press the down arrow to select any OS it will not move down so i can select Xp, the arrow wont move off Ubuntu .. so each time i start my pc it goes boots into the default OS (ubuntu) after 10 secs.
I boot into ubuntu  went into the grub menu list an select windows as my default OS an now i'm stuck in windows :( bcuz the down or up arrow wont move up to unbuntu so i can select it. during installion i used the default u.s standard as my keyboard of choice
I  kno my key board is ok cuz  i checked it myself .. is there a way i can fix this without Re-Installation

---

### Post by Joeb454 on 2008-02-22
Is the keyboard a USB keyboard?

If so check that it's enabled in your BIOS :)

---

### Post by seventhc on 2008-02-22
I know of a similar issue someone had and they had to reset their BIOS to default settings. This isn't an OS issue since the keyboard should be one of the first things loaded during boot-up. Since your keyboard isn't loading you wouldn't even be able to get into the BIOS by keyboard. You would have to physically remove the battery( it looks like a watch battery) and let it sit for a while until it resets to defaults.

On some boards, it can take up to an hour to reset, but some will reset in a matter of minutes.
I'm not sure if this is the case for you, but like I said before, the keyboard should load before you get your choice of OS's

[COLOR=Red]**Note[COLOR=Black]:[/COLOR]** If you do this, touch a part of the computer chassis that's made of metal to discharge any static in your body first.[/COLOR]

---

### Post by SILLAT on 2008-02-22
Its A Usb Keyboard
I'm Not Home Now So I Dont Kno If Its In The Bios But It Shud Be In There Its Been On My P.c For Months Now
Do U Think A Serial Will Work Out Better

---

### Post by seventhc on 2008-02-22
If you have a serial, I would try it. It would at least narrow down what's wrong. :)
Then you would be able to get into your BIOS to check the settings.

---

### Post by Joeb454 on 2008-02-22
Try a serial keyboard to see if it works, if not try post #3 :)

---

### Post by SILLAT on 2008-02-22
I Dont Hav A Problem Getting Into The Bios With My Present Keyboard
Its Jus The Arrows Not Moving Downwards To Select The Os.
It Works Perfecty Fine In Windows So Wat Cud Cause This Problem Now

---

### Post by freelinuxhelp on 2008-02-22
Just get a USB - PS2 adapter.

---

### Post by seventhc on 2008-02-22
oh, so the keyboard is working, just not the arrow keys??? :confused:
Have you tried the arrow key's when in the OS. Like test that they work there, have you spilled anything on it lately???

---

### Post by SILLAT on 2008-02-22
i use my arrow keys in windows an it very worked well
i dont remembe rusing my arrow keys in ubuntu wen i 1st got in
i dont spill anything on it or pull it apart. .never

---

### Post by y-lee on 2008-02-22
you can might be able to use [super grub disk]("http://supergrub.forjamari.linex.org/") to boot into ubuntu. You have to download the ISO and burn it and be able to boot into a cd.

---

### Post by philinux on 2008-02-22
> **SILLAT said:**
> i use my arrow keys in windows an it very worked well
i dont remembe rusing my arrow keys in ubuntu wen i 1st got in
i dont spill anything on it or pull it apart. .never

Without rebooting my machine I think you need to press the ESC key as soon as grub appears on screen, then you can use the arrow keys. The 10 sec delay is so you can press ESC.

---

### Post by seventhc on 2008-02-22
You have to press escape first???
I don't remember having to do that when I had a dual boot...but it would explain why other keys are working but not the arrow keys.
If this works, I'll have to remember this for future reference. :)

---

### Post by Joeb454 on 2008-02-22
Does pressing escape work?

If so it probably means you have your boot menu hidden.

---

### Post by seventhc on 2008-02-22
> **Joeb454 said:**
> Does pressing escape work?

If so it probably means you have your boot menu hidden.
If I understand correctly, the boot menu is showing up, but no selection can be made by using the arrow keys. So it just boots to the default selection.

---

### Post by webjames on 2008-02-22
When in the grub (bootloader) menu can you press esc and see if it stops the time counting down, if so that narrows it down to the arrows, not the keyboard.

Grub normally starts the default system after a few seconds. esc will stop this.

---

### Post by SILLAT on 2008-02-22
hey thank u all for ur expert advice . . as soon as i get home later  i'll try them all them post a  new reply

Hey[COLOR="Red"] Seventh[/COLOR] thats exactly wats happening. . the boot menu is showing up, but no selection can be made by using the arrow keys. So it just boots to the default selection.

---

### Post by seventhc on 2008-02-22
I think still try pressing the 'esc key' as posted earlier while in the menu...it never hurts to try
so when in menu..<Esc> <arrow>

---

### Post by SILLAT on 2008-02-22
hey[COLOR="Red"] UBUNTU HELPERS[/COLOR] thank u all for ur advise .. my booting problems are ova :)
I was using a USB mouse with my p.c an wen i press the Escape then the arrow key nothin happened it jus boot into the default OS :confused:
But wen i changed my keyboard to a  serial (ps/2) keyboard an press the escape then the down arrow surprisingly it moved  so i selected ubuntu an i'm on ubuntu now posting a thank u reply . .. :lolflag:
you guys are tha best :guitar:

---

