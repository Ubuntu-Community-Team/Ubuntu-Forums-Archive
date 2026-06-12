---
title: "default sound card"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-04
Anyone know how to set up my usb sound card (its for a pair of headphones) so whenever I hook it up it becomes the default sound card?

I can set it up once in the sound settings:

[IMG]http://img501.imageshack.us/img501/4262/screenshot3rq0.png[/IMG]

but it goes away after I disconnect the usb sound card and then reconnect it later.

It goes back to this:

[IMG]http://img525.imageshack.us/img525/3840/screenshot2bg4.png[/IMG]

Let me know thanks!

---

### Post by userundefine on 2007-01-04
Connect both cards.  In a terminal, type:

**sudo asoundconf list**

This will print out all sound cards you have.  Then, use this command to set your default choice.

**sudo asoundconf set-default-card CARD**

where **CARD** is your desired card as printed out by the first command.

---

### Post by zmuth734 on 2007-01-04
> **userundefine said:**
> Connect both cards.  In a terminal, type:

**sudo asoundconf list**

This will print out all sound cards you have.  Then, use this command to set your default choice.

**sudo asoundconf set-default-card CARD**

where **CARD** is your desired card as printed out by the first command.

Hey thanks!

I get this when I type in sudo asoundconf list:
```
Names of available sound cards:
ICH6
default
```

I'm assuming default is the name of the c-media usb headphone set?

---

