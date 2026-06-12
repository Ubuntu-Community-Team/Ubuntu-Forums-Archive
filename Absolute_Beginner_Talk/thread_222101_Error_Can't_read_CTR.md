---
title: "Error: Can't read CTR"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by N84 on 2006-07-24
After I start ubuntu I get a message after about 20 seconds that says “Can’t read CTR”. Then a few seconds later it continues the normal boot process. I just installed ubuntu. I don’t know if x is suppose to run right away but it stays in the terminal and locks up at the user login. The keyboard doesn’t respond and when I hit num lock the light doesn’t change. I switched keyboards just to make sure that wasn’t it. I also tried booting in rescue mode but to no avail. Any ideas?

---

### Post by luna2006 on 2006-10-25
hello everybody,

I have same problems with the 686smp kernel on dapper and also with the generic kernel on edgy.My keyboard and my mouse too don't work ; it is as they are not connected on my computer.Both are ps/2

I got that error : [COLOR="Red"]i8042.c: Can't read CTR while initializing i8042.[/COLOR]

Can someone help me?

Thanks

---

### Post by razzo on 2006-10-27
I have same problems with a fresh edgy install .

Only booting in rescue mode ( ro single ) i can start gdm with working PS2 mouse and PS2 keyboard .

In the *default boot* my keyboard and my mouse don't work .
If i switch mouse from PS2 to USB start working , but keyboard still don't work .

The error is the same previously posted : 
"i8042.c: Can't read CTR while initializing i8042" .

Any Ideas ?

---

### Post by razzo on 2006-10-27
I solve the problem passing acpi=off in grub.
There is a bug in acpi keyboard controller .

---

### Post by razzo on 2006-10-27
...or simply disabling usb keyboard and usb mouse from bios , so acpid can turned on ;)


In fact the problem , after some searches , is due to a *conflict* between i8042.c keyb. - mouse controller and the bios usb keyb - mouse emulation .
There is a new kernel facility "usb-handoff" 	
that it would have to solve this problem , but seem it doesn't work .


I hope that this thread can help someone .

---

### Post by luna2006 on 2006-11-02
thanks !

acpi=off works great !
I will try later for usb-handoff.

luna

---

