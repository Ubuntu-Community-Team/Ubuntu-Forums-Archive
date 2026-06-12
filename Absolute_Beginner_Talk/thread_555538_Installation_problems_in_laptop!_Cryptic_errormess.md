---
title: "Installation problems in laptop! Cryptic errormessages..."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Tilulii on 2007-09-20
Still having installation problems. The IBM ThinkPäd refuses to become a Ubuntu-computer!

I used to have problems like this:

```
[0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[181.563259] invalid compressed format (err=1)
[181.581722] Kernel panic - not syncing: VFS: Unable to mount roof fs on unknown-block(104,1)
[181.581968]

```

But I upgraded to problems like this:
:)
```
[0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[233.378507] invalid compressed format (err=1)
[233.396999] Kernel panic - not syncing: VFS: Unable to mount roof fs on unknown-block(104,1)
[233.397245]
```

The error message changed when I switched harddrives... Funny, I say!

The machine is following:
IBM ThinkPad 600X
Memory 320Mb, interestingly there are two 128Mb thingies in it, and from somewhere there comes an additional 64 MB. Beats me?

Don't relly know what to do, any help there?

---

### Post by Tilulii on 2007-09-20
Whoa!

New error messages! The standard ideology of 'if you do not know what to do, do something' worked! Well... Working is maybe too hasty, but a new error!

Tried to boot with boot:live acpi=off
And it truly does something!

```
[XXX.XXXXXX] atkbd.c : Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly
```

The XX.XXXXXX part can be replaced with a number, as the errormessage comes all the time, over and over, with a rising number... 

Still no install though  :)

---

