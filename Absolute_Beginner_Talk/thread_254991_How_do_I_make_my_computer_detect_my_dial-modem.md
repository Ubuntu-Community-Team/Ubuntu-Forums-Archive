---
title: "How do I make my computer detect my dial-modem"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-09-10
I used GnomePPP to try to connect online but it said that there was no dial-up modem detected, any ideas?

---

### Post by UltraMathMan on 2006-09-10
Iirc modem support is spotty in Linux because of the way most modems operate (the OS is expected to do some of the work, but what and how much isn't exactly always clear). Do you know what type and model modem you are using?

---

### Post by anubis2814 on 2006-09-10
no I don't know the model unfortunately any ideas, how I could find it easily and if I do how do I make it recognized

---

### Post by UltraMathMan on 2006-09-10
post the output of 

lspci -v

and is it a brand name computer? If so could you give the brand and model?

---

### Post by anubis2814 on 2006-09-14
0000: 01: 0e.0 Modem: PCTel Inc HSP Micromodem56 (rev02) (prog - if 04 [ Hayes/16750])

Subsystem: PCTel Inc HSP Micromodem56

Flags: Medium devsel, IRQ 10

I/O ports at 3400 [size = 64]

---

### Post by UltraMathMan on 2006-09-14
It seems that you modem belongs to that class of modems which are hard to get working in Linux. [This]("http://www.faqs.org/docs/Linux-mini/PCTel-MicroModem-Config.html") might be helpful with configuration.

---

### Post by helmut_hed on 2006-09-27
That one's a bit out of date - there's a specific FAQ for PCTel on Ubuntu located here:

[http://ubuntuforums.org/showthread.php?t=171163](http://ubuntuforums.org/showthread.php?t=171163)

I believe your modem should work with no trouble.

Regards,
Jeff

---

