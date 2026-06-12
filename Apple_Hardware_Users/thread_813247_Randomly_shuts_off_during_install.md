---
title: "Randomly shuts off during install?"
date: 2008-05-30
forum: Apple Hardware Users
---

### Post by uberamd on 2008-05-30
I am trying to install Ubuntu on my PowerMac G5 desktop system. The first PowerPC Desktop ISO for 7.10 wouldn't even load up, so I downloaded the alternate disc which loads into the text install. However every time I try to install the OS, the system just shuts off. It doesn't feel hot (so I am 99.9999995% sure over-heating isn't the cause). It seems to happen around the time I start typing in the new user-name. Around that point, the system without warning just shuts off, no errors, no cause, no reason from what I can see, it just dies.

Has anyone experienced this. The idea is to use the G5 as a image server for our local network using Ubuntu, however the install is a major pain to say the least compared to other architectures. 

Thanks for any advice.

---

### Post by Bakon Jarser on 2008-05-30
Did you check the md5 sum on the iso you downloaded.  If the md5 sum checks out ok then try burning the image slower (maybe 4x).

---

### Post by uberamd on 2008-05-30
> **Bakon Jarser said:**
> Did you check the md5 sum on the iso you downloaded.  If the md5 sum checks out ok then try burning the image slower (maybe 4x).

It shuts down at random times which leads me to believe it is not a disc issue.

---

### Post by attenpeter on 2008-05-31
Hi,

a friend of mine got these kind of errors on a non-apple-notebook and it turned out that his ACPI was broken... Try to disable ACPI when the installation CD kernel boots (append 'noacpi' to the kernel boot line [press F6 in the boot menu to show it]) and see if the crashes still keep happening...

EDIT: it must be "acpi=off", not "noacpi"; i confused that with "noapic", sorry.
EDIT2: that is, IF powermacs have acpi, which I'm not sure of and google won't tell me...

cu,
peter

---

### Post by stream303 on 2008-05-31
Maybe something overtaxing the power supply - I had a cdrom device go bad on me once that would just get hung for a little bit, and pull down the power supply.  The only way I could install was to burn at 2x speed, even though it could read faster, and eventually ended up replacing the cdrom.

Not saying that's your problem, but something to look at.  Anything inside causing shorts - large dust-bunnies? :)

---

