---
title: "Ubuntu Shutdown issues"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by subzero1266 on 2007-04-20
Hello,
 I have an irritating issue. Whenever I shutdown the computer, Ubuntu (happens in Dapper, Edgy and Feisty Fawn) shows the splash screen and all the LEDs turn off. But the CPU, heatsink fan still rotates. I have to press the power button on the cabinet to turn it off. Ubuntu reboots fine. Whenever I do shutdown, I have to wait and then press power button:(

I didn't have this problem with distros like Suse. Windows too shuts down correctly. I will be grateful to anyone who can help me in this matter. Thank you.

My hardware -
Intel P4 520 2.8Ghz HT
Motherboard: ECS 915 M5-GL

---

### Post by kevinlyfellow on 2007-04-20
what happens when you shut down like this
```
shutdown -P now
```

---

### Post by subzero1266 on 2007-04-20
> **kevinlyfellow said:**
> what happens when you shut down like this
```
shutdown -P now
```

Thanks for the fast reply.

I just tried the command. It gave me the same result. I had to press power button to turn off :(

---

### Post by subzero1266 on 2007-04-20
Does this something to do with ACPI ?

---

### Post by Pobega on 2007-04-20
Does /sbin/halt do anything differently?

If you're just issuing "shutdown" you're doing it wrong, it's classically done with "shutdown -h now"

---

### Post by kevinlyfellow on 2007-04-20
> **Pobega said:**
> Does /sbin/halt do anything differently?

If you're just issuing "shutdown" you're doing it wrong, it's classically done with "shutdown -h now"

The P option is for power off, which shuts down the power after the shutdown process.  

I think it is some sort of acpi issue

---

### Post by jalbatros on 2007-04-22
Hi, I had the same problem, and Saint Google helps me.
Here you have the solution that works in my PC, may be in yours too ...

1. Edit /etc/modules with "$ sudo gedit /etc/modules" and add a new line: "apm power_off=1"

2. Edit Grub menu with "$ sudo gedit /boot/grub/menu.lst" and look for the line with the kernel option you use normally (Ubuntu, kernel 2.6.20-15-generic in my own), at the end of this line add "acpi=off apm=power_off", without quotes of course.

3. Now you have to restart your PC in order that changes take effect.

Try it, good luck.

---

### Post by Sreekant on 2008-06-17
> **jalbatros said:**
> Hi, I had the same problem, and Saint Google helps me.
Here you have the solution that works in my PC, may be in yours too ...

1. Edit /etc/modules with "$ sudo gedit /etc/modules" and add a new line: "apm power_off=1"

2. Edit Grub menu with "$ sudo gedit /boot/grub/menu.lst" and look for the line with the kernel option you use normally (Ubuntu, kernel 2.6.20-15-generic in my own), at the end of this line add "acpi=off apm=power_off", without quotes of course.

3. Now you have to restart your PC in order that changes take effect.

Try it, good luck.
Thanks a lot . This solution of yours immediately solved my issue. The issue I'd was that the Ubuntu was installed on my Laptop alongwith Vista Basic. It booted & started well but while shutting had to be forcefully shut down using the 'power on/off' button.
MOdifying the 2 files & restarting the system has solved the issue. 
Thanks again.
regards
Sreekant

---

### Post by MichaelSwengel on 2008-06-17
> **subzero1266 said:**
> Does this something to do with ACPI ?

That's what I'm thinking. Although, I'm not sure how to fix it. 

If I were you, I would Google the model of computer you have and see what power issues other Linux users have had. I suspect that it's not limited to Ubuntu - although some Linux distros (*cough* PCLinuxOS *cough*) don't have good power management abilities.

So, something about your hardware doesn't like Linux's power system. Fortunately it still runs!

Sorry I'm not much help, but definitely look into that possibility.

Regards,
MS

---

