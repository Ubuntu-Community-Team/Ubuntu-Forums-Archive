---
title: "Mysterious errors and shutdown"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by user007usa on 2006-12-18
Every once in a while I will hear two error like beeps and then there will be a pause and ubuntu will then crash and shutdown itself.  No error messages are displayed.  

I have noticed that it happened more often with some applications running, so I quit using those.  But the other night I happened to hear the beeps at night when they woke me up.  Sure enough the next morning, the computer was off.

I checked /var/log/messages and there really wasn't anything incriminating at all nor an indication of what went wrong.

It does not seem as if the computer is over heating or anything either.

Possibly related:

I have KDE installed over the default Ubuntu installation.  It was around this time I started noticing it although it seemed to be certain applications doing it more.

I installed AVG free for linux and have it set to scan around this time at night.  From the AVG logs it seems that every once in a while for whatever reason it wasn't able to complete the scan.  But this doesn't explain it all as I don't think ubuntu should be crashing like this.  Certainly without error messages.  And this mysterious "two quick beeps thing" without error messages, even in syslog have me confused.

Help please?

---

### Post by tageiru on 2006-12-18
The two beeps could be motherboard error codes, check the motherboard manual.

Mysterious crashes without panics in /var/log/messages are usually hardware related.

---

### Post by Sef on 2006-12-18
Motherboard Errors:

[PC Hell]("http://www.pchell.com/hardware/beepcodes.shtml")

[Panther]("http://www.pantherproducts.co.uk/Articles/Motherboard/BIOSbeep.shtml")

---

### Post by user007usa on 2006-12-18
> **Sef said:**
> Motherboard Errors:

[PC Hell]("http://www.pchell.com/hardware/beepcodes.shtml")

[Panther]("http://www.pantherproducts.co.uk/Articles/Motherboard/BIOSbeep.shtml")

Thank you both of you.  I have a emachines desktop T2080 system.  I saw that it has a Phoenix bios.  Upon looking the codes are usually three, not two though.  Unless maybe the 2-_-_ counts too?  I will run Ubuntu's memory check and post results.

---

### Post by user007usa on 2006-12-18
I did one pass with memtest86 (took a little over 30 minutes)and it came out with zero errors.

But I notices I actually have the Phoenix AWARD Bios (v6.0.0) and that apparently these can vary because the computer maker can customize them. The beeps sound different though, like one is a high pitch and low pitch.  One site suggested CPU error I think?

I wish there was a way to be SURE about this stuff.  Seems funny that it is an intermittent thing and it isn't a POST error as this happens when the computer is on for several hours or even days.

Is there no other explanation for this or maybe other error logs to check besides /var/log/messages?

---

### Post by mongooseman1128 on 2006-12-18
try to download eurosofts hardware diag package, burn the CD and run the processor and MOBO tests

---

### Post by user007usa on 2006-12-22
As it turns out it was probably software related.  Two days ago I upgraded to Edgy (6.10) from dapper.  Since doing so, no problems whatsoever.

---

