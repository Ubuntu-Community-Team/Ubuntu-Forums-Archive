---
title: "new video card problem"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-10-29
i just got a new video card (GeForce fx 5200) upgrading from an intel integrated graphics card. when i boot up the Ubuntu loading screen never fully loads, it always loads about 1/10 of the way then stays there at a standstill. then i switch it back to my old integrated card and it boots up fine.

i went into verbose mode and the last two responses i get were:

[28.999289] [<c02f0000] clip_ioctl+0x500/0x510
[28.999408] ================

then i checked the bios and the only options to change my "primary video adapter" to were auto and onboard (i think both of those would be the integrated controller)

any suggestions on how to get the computer to start?
thanks in advance

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> i just got a new video card (GeForce fx 5200) upgrading from an intel integrated graphics card. when i boot up the Ubuntu loading screen never fully loads, it always loads about 1/10 of the way then stays there at a standstill. then i switch it back to my old integrated card and it boots up fine.

i went into verbose mode and the last two responses i get were:

[28.999289] [<c02f0000] clip_ioctl+0x500/0x510
[28.999408] ================

then i checked the bios and the only options to change my "primary video adapter" to were auto and onboard (i think both of those would be the integrated controller)

any suggestions on how to get the computer to start?
thanks in advance

Here try this, post the following output:
```
glxinfo
```

---

### Post by onearmedpanda on 2007-10-29
where do you want me to type that?

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> where do you want me to type that?

In the Terminal.

---

### Post by onearmedpanda on 2007-10-29
i can't get to the terminal because i can't get ubuntu to start
it's freezes while it's loading

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> i can't get to the terminal because i can't get ubuntu to start
it's freezes while it's loading

You're going off the LiveCD correct?

---

### Post by onearmedpanda on 2007-10-29
no
ubuntu is installed already

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> no
ubuntu is installed already

Have you tried installing Ubuntu through the alternate installer CD?

---

### Post by onearmedpanda on 2007-10-29
yes that is how i originally installed it because my bad integrated video controller was giving me problems with the normal disk
should i just reinstall ubuntu?

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> yes that is how i originally installed it because my bad integrated video controller was giving me problems with the normal disk
should i just reinstall ubuntu?

I would attempt to, but it sounds to me like you have a hardware issue.

---

