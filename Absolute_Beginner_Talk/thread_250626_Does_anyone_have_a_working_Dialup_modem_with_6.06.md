---
title: "Does anyone have a working Dialup modem with 6.06?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by bryan4134 on 2006-09-04
I have spent hours trying to get both internal WinModem as well as external USB modem to work.  Maybe I am dumb but after pages and pages of tech-speak I am still no further forward. I am quite happy to buy a new modem (dialup not ADSL) if there is a chance it may work without too much need to be techie.

I normally use broadband but I travel a lot in places where it simply not available - hence the need for dial up.

Appreciate any thoughts.

Bryan

---

### Post by Bachstelze on 2006-09-04
Any SmartLink based modem will do the trick :) Up and running with one package from the repos installed.

---

### Post by bryan4134 on 2006-09-04
Thanks - are they USB or PCMCIA modems? On a laptop so no serial ports.  Any suggested brands?

Thanks again.  Bryan

---

### Post by whizbaby on 2006-09-04
>open a terminal, type

**sudo wvdialconfig**

>then edit your /etc/wvdial.conf (e.g. by **sudo nano /etc/wvdial.conf** ) and fill in your username, password and provider phone number (it's at the bottom). Save, leave editor and type 

**sudo wvdial**

(Encountered only one modem (a LoseModem,too) not detected. Only my personal experience.)
Still no connection? (or did you try that already?)

---

### Post by Bachstelze on 2006-09-04
How is that supposed to work if the modem drivers are not installed ?

bryan4134, well, mine is a laptop too but the modem is built-in so I don't know how they are retailed. But anyway, I think you should be able to get yours working too. Have you followed the instruction at [www.linmodems.org](www.linmodems.org) ?

---

### Post by whizbaby on 2006-09-04
@hymntolife:
Because wvdial does not need ANY driver to work. Wvdial intelligently determines how to talk to your modem. Type **man wvdial** to learn more (and of course **man wvdialconf**, too).

---

### Post by Bachstelze on 2006-09-04
I've had three winmodems and none of them worked with wvdial until drivers are installed... And anyway, it won't work because the wvdialconfig command does not exist, it's wvdialconf.

---

### Post by whizbaby on 2006-09-04
> **whizbaby said:**
> 
(Encountered only one modem (a LoseModem,too) not detected)

Already wrote that there might be problems with it. Bryan4134 said that he had another modem so I thought it might be useful to try to get this to work before buying a new one.
(thank you for correcting my **typing error**)

---

### Post by bryan4134 on 2006-09-04
Tried this.... but no modem located....  see below. Now heading over to linmodems.org.....  thanks for the ideas - keep them coming!

bryan4134@bryan4134-laptop:~$ sudo wvdialconf
Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
Modem Port Scan<*1>: SHSF0 S0   S1   S2   S3   S4   S5   S6
Modem Port Scan<*1>: S7   S8   S9   S10  S11  S12  S13  S14
Modem Port Scan<*1>: S15  S16  S17  S18  S19  S20  S21  S22
Modem Port Scan<*1>: S23  S24  S25  S26  S27  S28  S29  S30
Modem Port Scan<*1>: S31  S32  S33  S34  S35  S36  S37  S38
Modem Port Scan<*1>: S39  S40  S41  S42  S43  S44  S45  S46
Modem Port Scan<*1>: S47  SHSF1 SHSF2 SHSF3 SHSF4 SHSF5 SHSF6 SHSF7


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

---

### Post by Bachstelze on 2006-09-04
linmodems did it for me. Justget the scanmodem tool, launch it, send the modemdata.txt file to the mailing list and nice volunteers will tell you how to get it working :)

---

### Post by whizbaby on 2006-09-04
Only to know:
What brand is your not-detected usb-modem (don't want to accidentially buy one)?

---

