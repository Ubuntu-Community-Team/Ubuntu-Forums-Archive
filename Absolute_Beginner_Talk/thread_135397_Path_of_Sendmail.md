---
title: "Path of Sendmail"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by BobSongs on 2006-02-23
Well. I'm stumped.

Nautilus crashed. Up popped the "Bug Buddy" and I filled in some fields. Then clicked "Next". Now I'm at Mail Configuration. It asks:
> Bug Buddy uses email to submit the bug reports.
Please choose how you would like Bug Buddy to send email:
(x) Use Sendmail directly
( ) Just save to a file so I can submit a bug report manually

**Sendmail settings:**
Name: Blah blah
Email: [email]blah@blah.bla[/email]
Path of sendmail:_______________Whaa? I don't know where sendmail's located. Anybody? I'd like to send in bug reports. But I can't advance in this dialog until I get past this.

I tried:```
$ whereis sendmail
```but I only got> sendmail: as my answer. Google didn't help much.

Thanks, dudes!

---

### Post by Cephyr on 2006-02-23
Did you try just entering "sendmail" into the path box? I'm not sure if that could work, but it seems like it should.

---

### Post by BobSongs on 2006-02-23
[QUOTE=Cephyr]Did you try just entering "sendmail" into the path box? I'm not sure if that could work, but it seems like it should.[/QUOTE]
It returns the lovely error: > 'sendmail' doesn't seem to exist. Please check the path to sendmail again.

---

### Post by anil_robo on 2006-03-03
Open synaptic and search for sendmail. Then install it from there.

Sendmail will then be found in /usr/sbin/sendmail

---

### Post by BobSongs on 2006-03-04
[QUOTE=anil_robo]Open synaptic and search for sendmail. Then install it from there.

Sendmail will then be found in /usr/sbin/sendmail[/QUOTE]Alright! Sendmail installed. Now I'm almost eager for Nautilus to crash to test it.

:-k Hmm. That's probably weird. Thanks again.

---

