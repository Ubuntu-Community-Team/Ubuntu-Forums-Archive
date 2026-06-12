---
title: "Booting on a Dell Dimension 2350"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Ophidian on 2007-04-05
Hello, I'm still having issues with Ubuntu on my Dell Dimension 2350 machine (only 128 MB of RAM) 

Here's what I'm doing:
-Switching to boot from CD in BIOS
-Insert Ubuntu live CD into drive
- Wait ...
- A text reading "Cannot find drive to boot from, press F2 to enter setup!"

The thing is, this isn't limited to simply Ubuntu. Some other distros I try to install go through a similar process with the same results, although I've nearly gotten a version of Knoppix to load and just freeze up.

Also, booting from USB doesn't seem to be an option. I wish it were. 

Any input?

---

### Post by Feba on 2007-04-05
Sounds like your PC is really old.. might be the drives dying.

---

### Post by LaurelLynn on 2007-04-05
Dear Ophidian,

Sounds like your bios is not set to boot from the cdrom (that is common).

You could hit F2 and change the settings under the boot menu.

Or if that is a bit much for you, there is usually a function key (F10 on mine, maybe F12)
that takes you to a menu of possible boot devices. Pick the cdrom.

Hope that helps.

Laurel Lynn

---

### Post by Ophidian on 2007-04-05
> **Feba said:**
> Sounds like your PC is really old.. might be the drives dying.

Old by most computer standards, as the machine itself is 4 years old (It has a pIII processor)... but, I've run Ubuntu on machines that were WAY older, stuff that has pII--that old. If you mean CD drive, that might be a possibility--but in Windows, I can read CDs just fine.

---

### Post by Ophidian on 2007-04-05
> **LaurelLynn said:**
> Dear Ophidian,

Sounds like your bios is not set to boot from the cdrom (that is common).

You could hit F2 and change the settings under the boot menu.

Or if that is a bit much for you, there is usually a function key (F10 on mine, maybe F12)
that takes you to a menu of possible boot devices. Pick the cdrom.

Hope that helps.

Laurel Lynn

<<
Here's what I'm doing:
-Switching to boot from CD in BIOS
>>

---

### Post by LaurelLynn on 2007-04-05
If the bios truly is starting with the cdrom drive, and still can´t read it. I would agree with Feba, there is probably a problem with the drive. Especially as you haven´t been able to boot from other disks.

If you still have an old os (such as windows, oh the shame) on the drive, I would boot to it. Then see if I could play music CDs or read some programs installation disk.

If not, I would check all the connectors on the cdrom drive. They get loose and sometimes accumulate corrosion over the years.  Sometimes just unplugging and replugging the IDE cable fixes the problem.

Only then would I think about replacing it.

Laurel Lynn

---

### Post by Feba on 2007-04-05
If you have a new (or older, for that matter) PC sitting around, you could probably take a CD drive out of it to test.

Keep in mind that Ubuntu should have at least 256MB of RAM. 

You might find that a small distro, such as DSL or Puppy will work better on your system.

---

### Post by LaurelLynn on 2007-04-05
I was thinking the same thing, Feba, about using a drive from another PC. Memory might be a problem latter, but if it is the bios that is complaining, memory is not an issue yet.

Laurel Lynn

---

### Post by Feba on 2007-04-05
If he got close to getting Knoppix to boot, then it may be that the distros he's trying just aren't compatible with his system, which would likely make the bios reject it

---

### Post by LaurelLynn on 2007-04-05
It is possible Feba.

However since his original post said "Cannot find drive to boot from, press F2 to enter setup!". I still think it may be a drive problem. At that point I believe bios hasn´t even read the contents of the disk, it´s inability to do so is what it is most likely complaining about.

Hardware problems like bad connections are very common, and often produce intermittent results like locking up at different points during bootup.

At least that´s my feeling.

Laurel Lynn

---

