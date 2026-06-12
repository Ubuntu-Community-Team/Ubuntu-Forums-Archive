---
title: "Ubuntu install fail"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by merobertd on 2007-03-10
Hi
I have an old Dell 2350 with pentium 4 2.5 Ghz 528 mb ram a built in graphic card 60 Gig HDD
there is no OS on it but it did run XP well.

I and tried to install 
Ubuntu 6.06,6.10 Cd iso and dvd iso
and afew other versions of linux but they all failed.

When i get the boot menu up i have tried 

Start Ubuntu & in safe graphics mode
The cd pass no defects, but i tried others anyway
i have pressed F6 and entered

ide=nodma

irqpoll pci=noacpi noapic nolapic acpi=off

But no luck can anyone please help me i dont want to go back to MS



i get to the forth picture down
then it flys through lots of white text and i have to turn off the power.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Delvien on 2007-03-10
> **merobertd said:**
> Hi
I have an old Dell 2350 with pentium 4 2.5 Ghz 528 mb ram a built in graphic card 60 Gig HDD
there is no OS on it but it did run XP well.

I and tried to install 
Ubuntu 6.06,6.10 Cd iso and dvd iso
and afew other versions of linux but they all failed.

When i get the boot menu up i have tried 

Start Ubuntu & in safe graphics mode
The cd pass no defects, but i tried others anyway
i have pressed F6 and entered

ide=nodma

irqpoll pci=noacpi noapic nolapic acpi=off

But no luck can anyone please help me i dont want to go back to MS



i get to the forth picture down
then it flys through lots of white text and i have to turn off the power.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)



Is this a laptop ?

---

### Post by merobertd on 2007-03-10
Sorry no its a desktop about 6 years old

---

### Post by chewearn on 2007-03-10
Can you post where the installation fails, or what error message(s) you are getting?

---

### Post by merobertd on 2007-03-10
i have had 2 error messages the first was something like 

respawing to fast disables for 5 minuites repeated 5 times. 

The one im looking at now is a bunch of numbers

[17179642.232000] [,c010412c.] apic_timer_ interrupt+0x1c/0x30

repated 18 times the first number is always the same but the second one changes & the text is diffrent for all of them.


Since i posted i tried the disk on another computer and it worked in Live mode so the disk is ok.

---

### Post by merobertd on 2007-03-10
the last line is [17179642.232000] code: 00 00 00 0f ba 35 88 ae 3d c0 00 e9 73 ff ff ff 8d 76 00 8b 44 24 04 50 6a 01 e8 84 9f 00 00 59 58 c3 90 ff 05 8c 2e 3d c0 31 d2 <87> 15 b0 d0 ff ff ba 00 e0 ff ff 21 e2 81 42 14 00 00 01 00 50

---

### Post by chewearn on 2007-03-10
Opps.  This one too deep for me.  Need expert help.

Do you get these same errors on both the ubuntu 6.06 and 6.10?

Also, not sure if it will make a difference, but did you try disabling ACPI or Power Management from the BIOS instead?

---

### Post by merobertd on 2007-03-10
I get the same errors for 6.06 and 6.10 cd iso
but i get a diffrent error of 6.06 dvd iso more text and code some thing about 

kernel panic - not syncing : fatal exception in interrupt


try disabling ACPI or Power Management from the BIOS instead

what is that and how do i do it

---

### Post by chewearn on 2007-03-10
> **merobertd said:**
> I get the same errors for 6.06 and 6.10 cd iso
but i get a diffrent error of 6.06 dvd iso more text and code some thing about 

kernel panic - not syncing : fatal exception in interrupt


try disabling ACPI or Power Management from the BIOS instead

what is that and how do i do it

During boot up, at the first screen (probably showing the Dell logo), you should see a message like "Press F6 to enter BIOS setup".  Press the button it indicated.  You should now see a text screen, with bunch of stuff that you can change; the first page should be where you can change the system time, date, etc.  Follow the instruction on how to move to the next page.  IIRC, you use CTRL+P or similar.  There should be a page on Power Management.

I'm trying to remember the Dell BIOS screen from memory; so forgive me if I got things wrong.  I used to have a Dell PC at work, but then switch to a Dell Notebook few years back.  At home, I have the much more common Award BIOS, which looks nothing like the Dell BIOS.

---

### Post by merobertd on 2007-03-10
i looked at all the disks just to see if there was a version i had not tried and there where two on the dvd.iso

text mode
and oem mode

i tried oem mode and it installed said it was done just had to reboot and config some password and it would be working.

When i rebooted with no disk in the drive the ubuntu logo came up & it started to load, but it has frozen with about 1/5 loaded for about 1/2 an hour now.

I will try the bios thing you suggested next.

i will also look for oem install posts as i have not looked for them before.

---

### Post by merobertd on 2007-03-10
> **AstalaVista said:**
> 

Also, not sure if it will make a difference, but did you try disabling ACPI or Power Management from the BIOS instead?

acpi options where s1 and s4 and i disabled the power management but made no diffrence

---

### Post by RickThorpe2006 on 2007-03-28
Try this:  in the LiveCD startup screen, hit the function button with VGA next to it (think its F4, but check the bar at the bottom of the screen).  Use the arrow key to change the option to 640X480.  Proceed with the safe graphics mode option.  My screen looked a bit scrunched, but I was able to complete installation on my 2350.  Once install is done, boot into ubuntu from the hard drive.  Go into preferences -- screen resolution and pick the appropriate option; at 640 or 800, your desktop should expand to find the screen for normal use.  Don't know why this works, but it worked for me -- ymmv.

---

