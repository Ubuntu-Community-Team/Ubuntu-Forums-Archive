---
title: "I &quot;cleared&quot; my &quot;extended system configuration data (ESCD)&quot;"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by kchukchukchu on 2006-04-18
Hello everyone,

In trying to get the install to work, I played with the BIOS on my HP Pavillion 6535 and boldly chose "YES" to the option clear extended system configuration data.

The system now does not see the CD-ROM drive nor the floppy drive when it boots and so the install CD doesn't even start.

I'd be happy if you'd tell me what I need to do to restore that.:(

THANKS in a advance,
Kay

---

### Post by trent dillman on 2006-04-18
Boot back into the bios and make sure the boot order is still the same. Or, just go in and turn it back on.

---

### Post by kchukchukchu on 2006-04-18
Hey Trent dillman, 

I DID!! In fact the next time I went in, it already said no (ie not clearing the ESCD) without me having to turn it back off, and I made sure the boot order is what wanted.  But the boot diagnostic screen is just different from before: ie. not CD-ROM OK, floppy -ok kind of statements.

thanks for your quick reply, I do appreciate it,
Kay

---

### Post by trent dillman on 2006-04-18
As a worst-case scenario, you could always flash the bios....

EDIT: Or open the case and reset the CMOS.

EDIT 2: Also check for PnP settings in the BIOS, see if they're turned off....

---

### Post by kchukchukchu on 2006-04-19
hello trent dillman,

Thanks for your reply!  

What I screwed up in the first place was I cleared the CMOS, and somehow the BIOS didn't detect the CD-ROM drive afterwards.  So, I cleared the CMOS (or ESCD) again, and it worked!!

Thanks:)
Kay

---

