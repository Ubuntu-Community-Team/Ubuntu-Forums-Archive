---
title: "Cannot boot live disc?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by freakboysystem on 2007-05-13
Hi, Please help i cannot boot from 6.06 or 7.04 live discs.
My system:
512mb ram
1.3ghz processor
dvd/cd
40gb hdd
is a i386 laptop
and boot from CD as top option.

what happens:
it comes up with Ubuntu boot menu
select 'Use Ubuntu live disc'
press enter
just say loading for 10minutes
then says error reading disc

(these are discs from 'Ubuntu' the ones they send you)

Appreciate any help.

---

### Post by orb9220 on 2007-05-13
> then says error reading disc

Well did you order more than 1 disc?
Did you try booting cd in another system to help whether it is the cdrom drive or actual disc?

Make a copy of the disc and try the copy?

---

### Post by freakboysystem on 2007-05-13
i have one 6.06 and 3 7.04's tried all 3.

---

### Post by nickpaton on 2007-05-13
At the boot menu run the check CD option to make sure there are no errors.

If there are no errors press F6 Other Options.

At the end of the command line which appears, type in:

```
noapic
```

If that doesn't work you could try change the BIOS to its default settings.

What is the make and model of the laptop?

---

### Post by freakboysystem on 2007-05-13
It's made by a ompany called MAXDATA i think there german.

---

### Post by nickpaton on 2007-05-13
Can you try the noapic solution and post the results back.

---

### Post by majickcatz on 2007-09-06
Hey guys
I'm having the same problem.  When I try any of the boot options - including 'Check CD for defects' , I get an I/O error message saying 'error reading boot CD' - 
Tried adding noapic to F6 - and still get the same response

At the top of the screen there is green writing saying:-

k error 7H, HX 47NH, drivr H7inux: Disk error 20. AX - 4280. drive 82inux: His

I tried burning a fresh disc from my PC - but the other disc doesn't even get that far.. - I thought the disc's might be damaged - what do you think ? - would it be worth buying fresh disc's and burning it again? - or have I done something wrong?

Any advice would be much appriciated

__________________

---

### Post by alienexplorers on 2007-09-06
Are you checking the MD5 checksum.  Are you burning the disk at 4x speed.  Lastly are you using a good quality cd to write the iso's to.

---

### Post by majickcatz on 2007-09-06
> **alienexplorers said:**
> Are you checking the MD5 checksum.  .

Yes


> **alienexplorers said:**
> Are you burning the disk at 4x speed..

Yes

> **alienexplorers said:**
>   Lastly are you using a good quality cd to write the iso's to.

Not too sure - I've never burned anything before and am using some of my fiance's disc's - they don't look too healthy tho....

Do you think poor quality disc's is the likely problem?  If not, any ideas of what else it could be ?

Thanks Again :)

---

### Post by alienexplorers on 2007-09-06
I tried some off brand cd's and had nothing but problems.  I try to stick with Maxell or TDK.

---

### Post by majickcatz on 2007-09-06
Anything is worth a try.
Will go shopping and will let you know what happens
Thanx :)

---

### Post by bigboy_pdb on 2007-09-06
If you purchase some CD-RWs, you'll be able to reuse them. I use TDK and they work well. I've also used these CDs on an older machine that was a Pentium II and it didn't have problems booting from them.

If either of you (majickcatz or orb9220) have slow internet connections, it might be a good idea to use torrents to download the Ubuntu ISOs or to download them using another person's fast internet connection.

**EDIT:** I made that last statement because orb9220 stated that he asked Ubuntu to send CDs.

---

