---
title: "Fan won't quit running"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-10-14
Hello.

I just installed Ubuntu Dapper on an older DELL GX110 PC.
The fan runs 24/7.

What can I do about this?

Best,
Tom

---

### Post by thomasaaron on 2006-10-16
I'm surprised there's not been an answer to this one.
I'm a bit worried my fan will burn out.
Has nobody else had this problem?

---

### Post by JayTee on 2006-10-16
is your system ACPI compliant? In other words does the BIOS support ACPI and is it turned on in BIOS? Also check to ensure your powernowd daemon is running.

---

### Post by gn2 on 2006-10-16
Dell Optiplex GX110 is a desktop PC, and the fans are supposed to run all the time.

If the noise is an issue, this is the site for you: [www.silentpcreview.com](www.silentpcreview.com)

---

### Post by kent41 on 2006-10-16
> **thomasaaron said:**
> I'm surprised there's not been an answer to this one.
I'm a bit worried my fan will burn out.
Has nobody else had this problem?

Can you open a terminal session and enter the following code to see if there is a task using most of you CPU time and causing the fan to run all of the time?

```
top
```

---

### Post by thomasaaron on 2006-10-17
Thanks guys. I'll check all of that out.

---

