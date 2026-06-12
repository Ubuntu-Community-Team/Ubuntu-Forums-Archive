---
title: "DVD's wont play"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by FNDII on 2007-08-04
When I first installed Ubuntu, I downloaded some codecs or something and DVD's would play fine.  Now for some reason they wont play at all, in any player.

The error I get from totem is "Could not read from resource"

I don't know what that means, or why it would suddenly stop working. more likely i cant remember why i was messing with to make it stop.

Is there a guide to dvd problems?

---

### Post by benx009 on 2007-08-04
can your system read dvds?  can you browse the contents of a dvd in nautilus?

---

### Post by TBerben on 2007-08-04
I had that problem too, solved it in one command.. Darn, I really should remember to save my fixes to text files... 

Ahh, found it, try running:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

The codec installer will install libdvdread3 for you (if everything goes right) but for some reason it fails to run this script. This solved it for me

---

### Post by FNDII on 2007-08-04
Yes i can view the DVD in NAt.

that command did not work, got this error


sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found

---

### Post by spur on 2007-08-04
As a quick and easy (dirty) fix try uninstalling al your players and codecs and reinstall. It looks to me like you have somehow deleted something, maybe while installing something else,
Do all the deletions with 'competely remove' so you can hope it has got rid of the lot and some setting does not  'kick in' and you have the same problems.
This should work as you had it working before.

---

### Post by benx009 on 2007-08-04
> **FNDII said:**
> Yes i can view the DVD in NAt.

that command did not work, got this error


sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found

i think it would be sudo cd /usr/share/doc/libdvdread3/examples/  and then do ./install-css.sh

idk if that'll fix your problem, but give it a shot:)

---

