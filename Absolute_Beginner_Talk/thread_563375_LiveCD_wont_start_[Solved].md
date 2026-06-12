---
title: "LiveCD wont start [Solved]"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-09-29
Hi, I'm installing Ubuntu on my laptop and when I restart the computer with the LiveCD, it doesn't give me the option to boot from the CD drive.

What can I do?

---

### Post by uknowho008 on 2007-09-29
there should be a key you press at post to choose what to boot from. usually f12 or f10 or something i think. or change your bios settings to boot from cd first also by pressing a button during post. usually del or one of the f keys. it depends on the laptop.

---

### Post by Cheese Roller on 2007-09-29
Tried it, there's nothing to configure boot order.

All F keys.

On another computer, I was able to easily configure boot order when pressing F8.

On this there is no option to.

---

### Post by Cheese Roller on 2007-09-29
No matter what option we click after pressing F8.

It brings this up.

Please select the operating system to start.

Windows XP Media Center Edition (bootscreen)
Windows XP Media Center Edition

Oddly enough, both lead to the same place.

---

### Post by uknowho008 on 2007-09-29
ive never heard of a computer thats unable to configure the boot order, but i could be wrong. what kind of laptop? look at the manufacturers website or your user manual to find out how to boot from cd.

---

### Post by Cheese Roller on 2007-09-29
It's a Qosmio Toshiba.

---

### Post by lisati on 2007-09-29
1. Is there an option to "Enter Setup" when you boot? If so, changing the boot order might appear under "Advanced"

EDIT: It might be F2 or ESC

2. On my Toshiba laptop, there's an option "Press F12 to change select boot device"

---

### Post by Cheese Roller on 2007-09-29
None of those worked either.

---

### Post by uknowho008 on 2007-09-29
are you sure it can read the disk?

---

### Post by st33med on 2007-09-29
You might want to see on boot what keys is "Startup" and "Boot Options" (or something like that). Once you have memorized that key, reboot once more, hitting that key *rapidly*.

---

### Post by lisati on 2007-09-29
> **uknowho008 said:**
> are you sure it can read the disk?

I agree - having faulty disks (or if they were incorrectly burned) can sometimes cause problems - if the disk was downloaded, the ISO file needs to be copied to CD with the "Burn disc image" option, NOT as a data disk.

Just a suggestion: My Laptop came with a recovery DVD. Somewhere in the manuals that came with it were instructions on using the recovery disk. These instructions might provide a clue on what to do to get your laptop to start from CD instead of the HD. (EDIT: I'm not suggesting you run your recovery CD! Just that the way it's used might provide a clue)

---

### Post by Cheese Roller on 2007-09-29
Sorry guys none of this is helping. Does Toshiba have Live Tech support? I looked but I could only find e-mail. I sent them an e-mail but the reponse time is being very slow.

---

### Post by Cheese Roller on 2007-09-29
No, the disc is good. I used this same one on another computer and the OS installed fine.

---

### Post by Sef on 2007-09-29
Have you tried pushing delete?

Update:  For Toshiba, use the [escape (esc) button]("http://www.michaelstevenstech.com/bios_manufacturer.htm").  

> 
Toshiba® 335 CDS 	ESC
Toshiba Protege 	ESC
Toshiba Satellite 205 CDS 	F1
Toshiba Tecra 	F1 o#F1EFA5r ESC

Toshiba Notebook [Newer models]
	

1. Turn on computer by Holding down power button while pressing the ESC key.
The machine will beep, then display:
Check System, then press [F1] key.
2. Release ESC key
3. Press F1 key

---

### Post by Cheese Roller on 2007-09-29
Nothing happened.

---

### Post by Cheese Roller on 2007-09-29
Thank you, thank you, thank you so much!!!! It worked!!

Off to install Ubuntu! Thanks once again.

---

### Post by lisati on 2007-09-29
> **Cheese Roller said:**
> Sorry guys none of this is helping. Does Toshiba have Live Tech support? I looked but I could only find e-mail. I sent them an e-mail but the reponse time is being very slow.

Don't hold your breath waiting.....sometimes companies have a reduced staff over the weekend.

---

### Post by lisati on 2007-09-29
A note for all Toshiba owners out there: there's an automated information system available @ [http://www.askiris.toshiba.com/ToshibaSupportSite/supportcentral/supportcentral.do?id=m1](http://www.askiris.toshiba.com/ToshibaSupportSite/supportcentral/supportcentral.do?id=m1)

---

### Post by Sef on 2007-09-29
> Thank you, thank you, thank you so much!!!! It worked!!

Off to install Ubuntu! Thanks once again. 

You're welcome.

---

