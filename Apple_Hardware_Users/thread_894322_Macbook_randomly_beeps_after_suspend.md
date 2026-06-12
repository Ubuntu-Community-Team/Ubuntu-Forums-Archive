---
title: "Macbook randomly beeps after suspend"
date: 2008-08-19
forum: Apple Hardware Users
---

### Post by piratenmartin on 2008-08-19
Hello Forum,

hopefully someone can help me with a strange problem I encounter from time to time when waking up my MacBook from suspend to Ram. I've searched a number of forums and googled a lot but so far have not found anybody posting the same issue:

Most of the time waking up the machine works perfectly normal but sometimes one can hear a series of beeps which sound kind of irritating ... the kind of sound one would expect when something is going wrong.

It never occurs when I boot OS X so I think a hardware problem can be excluded.

I don't know how to approach the problem how to get on with it.

Does anybody know how I can try to find out what causes the beeps?

System: Ubuntu 8.04 on a MacBook4 with C2D 2.2GHz 

Thank you in advance,

Martin

---

### Post by andybotting on 2008-08-19
I'm pretty sure I've had the same thing. Not every time, but every so often it would beep quickly, about 8 times or so. 

I've just compiled 2.6.27-rc3 and it's solved a whole bunch of small problems I was having. No more beeps :)

---

### Post by piratenmartin on 2008-08-19
Hey andybotting,

thank you for your fast reply and for pointing out a way the problem could be solved. I thought about compiling a kernel a while ago but didn't have time enough to do it in a proper manner.
I am still not planning to do it right now because I have a lot of other stuff to do. Could you maybe still send me your config file to save me some time if I do not get another hint on how to fix the beeping problem?

Martin

---

### Post by cyberdork33 on 2008-08-19
I have a Dell Inspiron 5100 that does the same thing on wake up, so it is not a Mac-specific issue. This is a not a high use machine for me though, so I have not tried to find the problem as I do not find it all that annoying. (I am happy it suspends at all).

Anyway, I thought that might help you in your search since you do not have to limit yourself to Mac-only forums and such.

---

### Post by apetresc on 2008-08-19
I have the same problem; it's definitely software based, because muting the volume (in software) before suspending always fixes the issue (if it was a hardware thing, it wouldn't care about your software volume setting).

Thus my temporary workaround that I use is to always mute before suspending, and unmuting right after.

---

### Post by cyberdork33 on 2008-08-19
> **AdrianP said:**
> Thus my temporary workaround that I use is to always mute before suspending, and unmuting right after.
You could probably script that and have it run automatically on suspend / resume.

You could also try configuring your machine to automatically unload / reload your sound modules on suspend. Check /etc/default/acpi-support

---

