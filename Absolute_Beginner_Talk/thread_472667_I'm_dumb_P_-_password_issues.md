---
title: "I'm dumb :P - password issues"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-13
I was changing my password today and was playing around with the random password generator (bad idea)

anyway... to make a long story short. I accidentally set a random password as my normal password (not knowing it) and logged off.


right now i'm booting from the live CD and i'd like to know the precise file where the password is stored so that i can get it back :)  [or at least find the random password so that i can write it down]


can i do this or am i screwed?

---

### Post by lazyart on 2007-06-13
Try booting into recovery mode (no CD, hit escape at the grub message).

Type passwd *username*
that should let you change it to something else.
while there, type passwd root
and change the root password to the same thing for simplicity

That should do it.

---

### Post by Tyke91 on 2007-06-13
thanks man :)

-tho i am concerned at the ease of getting into someone's computer...

---

### Post by HotShotDJ on 2007-06-13
First, take the LiveCD out of the computer... reboot ... hit "Esc" key when the GRUB prompt comes up.  Choose "recovery" option.  When it boots up, you'll be at a command line.  Type "passwd user" (without quotes and where user = the username for the account you messed up) -- I don't remember if you need to use "sudo passwd user" or not... if it doesn't work the first way, try the second.  You will be prompted for a new password.

EDIT:  Lazyart beat me to the "submit post" button. :)

---

### Post by Cypher on 2007-06-13
Rather than booting into the LiveCD. Choose the "Recovery" option from the GRUB menu, this will drop you to the command prompt as root. Here you'd type
```

passwd <username>

```
and put a password you can remember...

---

### Post by lazyart on 2007-06-13
> **Tyke91 said:**
> thanks man :)

-tho i am concerned at the ease of getting into someone's computer...

Good freakin' point there.

---

### Post by Atomic Dog on 2007-06-13
Yes.  This feature pokes some huge security holes into Ubuntu.

---

### Post by plcdfa on 2007-06-13
You can also password protect the grub menu if you like.  And  should also set a password on your BIOS setup so that no live cd may be booted. And still your data is only secured with the assumption that nobody has the opportunity to disassemble your machine. :D

---

### Post by lazyart on 2007-06-13
Did some looking around the forums.  To prevent this simple backdoor, set a root password:
```
sudo passwd root
```

---

### Post by plcdfa on 2007-06-13
I don't think that will prevent anyone from booting into recovery mode. :?:

---

### Post by HotShotDJ on 2007-06-13
> **Atomic Dog said:**
> Yes.  This feature pokes some huge security holes into Ubuntu.Physical access to the hardware is a huge security hole.  No software can fix that.  You can set a BIOS password to prevent booting from floppy, CD/DVD-ROM or USB ... you can set a GRUB password to prevent what you just did.  You can encrypt your partitions to prevent unauthorized access to your data.  BUT, if I have physical access to the hardware, I can reset the BIOS, rewrite GRUB and gain access to everything (with the possible exception to the encrypted stuff, depending on how you have it configured).  Ubuntu helps secure your system from attacks from the internet.  NO software can help you if a person gains physical access to your hardware.

---

