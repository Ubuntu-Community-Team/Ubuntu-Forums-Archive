---
title: "Print problems..."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by jackmc on 2007-04-04
Hello all,

I have just made the switch to linux (Ubuntu specifically) today. Here is what has happened:

Set up networking (pretty easy once I figured out what to do)

started finding my way around

was very impressed - can almost ditch windows.

I need some help though.. I cant print (not properly, anyway)

I have a Brother HL-5270DN laser printer connected directly to my router. It has served our 4 XP based systems well since we got it.

There is not a driver for this printer included in Ubuntu. I am using the 5170 driver (this could be the problem, but even as a noob I am doubtful)

When printing from openoffice Presentation (powerpoint equivalent), I get errors. first I got limitcheck, then I got memoryfull. These print out after one page (with 6 slides on it). Both seem to relate to the printers physical memory (I have printed out documents of the same complexity/lenght/size from XP with no hassles)

I have tried turning down the resolution, as i thought that this may decrease memory use - apparently not :)

If you can help, please do. Keep me away from MS :)

---

### Post by xopher on 2007-04-04
According to this: [http://openprinting.org/show_printer.cgi?recnum=Brother-HL-5270DN](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-5270DN)
it should work perfectly. So make sure you've got the correct driver installed for it :)

---

### Post by compmodder26 on 2007-04-04
What version of Ubuntu are you using (5.10, 6.06, 6.10, 7.04)?  I'm using 7.04 and I see that there is a driver for the HL-5270DN.

---

### Post by jackmc on 2007-04-04
Turns out its 6.10. I assumed it would be the latest one when I downloaded it :(

I have installed that driver (xopher), however it has far worse resolution, and does not allow duplex printing :(

should I upgrade to 7.04? Is taht difficult?

---

### Post by jackmc on 2007-04-04
xopher, I installed/selected it incorrectly... Now I have duplex mode, but I still get the "limitcheck" error when I use it.

---

### Post by jackmc on 2007-04-04
still can't get it to work, I've been at it all morning.

I have tried all the drivers I can find on Brothers page.

I have printed the document successfully from Windows, so the problem is not with the printer or the document.

Would upgrading to 7.04 fix my problems?

Any help would be appreciated

---

### Post by jackmc on 2007-04-09
Ok, I'm ready to move completely to Ubuntu, bar this one issue. Can anybody help me?

I have tried:

low resolution
different drivers
B&W/Greyscale (its a monotone laser printer)
Countless settings changes

Please help me :(

I am loving Linux, except this......

EDIT:
Ok, followed Brothers instructions again, and I can print without memory issues now, but Duplex mode won't work :(

I can live without it, but I like to save paper when I can

---

### Post by jackmc on 2007-05-02
Grr, broken in Feisty now :evil:

---

### Post by jackmc on 2007-05-02
SOLUTION:

Go in to printer Properties => Driver

Select 'Generic'

Find PCL 5e - this is the one you want

choose hpijs

Done :)

If you have issues, PM me. I worked for ages to get this to work (as you can see from this thread!)

---

### Post by jackmc on 2007-10-16
I'm glad i found this thread again - i just did the same thing in Gutsy, and got my printer working again :(

It was fine for quite a while in Gutsy beta, broke in the last few days...

---

