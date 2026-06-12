---
title: "how do i create an .iso"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-05-04
i have a disk that i would like to make an .iso image of. what application can i use to do this?

i want to have it for backup purposes in case i misplace or break the OEM disk.

---

### Post by jfinkels on 2007-05-04
> **pjones0404 said:**
> i have a disk that i would like to make an .iso image of. what application can i use to do this?

i want to have it for backup purposes in case i misplace or break the OEM disk.

One all-purpose program that I've found does many, many things is AcetoneISO. (It's a KDE app, so you'll need to install a couple dependencies as well).
```

sudo aptitude install acetoneiso

```
[http://www.acetoneteam.org/](http://www.acetoneteam.org/)

Or if you're comfortable with the command line, you can use "dd", (I think?)
```

dd if=/media/cdrom of=~/output.iso

```

CAREFUL with dd though: it will create a bit-for-bit copy of the input file at the output file location, even if it overwrites something.

---

### Post by mustang on 2007-05-04
> **jfinkels said:**
> One all-purpose program that I've found does many, many things is AcetoneISO. (It's a KDE app, so you'll need to install a **couple dependencies** as well).


And just to be clear, your package management software (in this case, aptitude) will handle that for you. You won't need to do anything in addition to the command provided.

---

### Post by jfinkels on 2007-05-04
> **mustang said:**
> And just to be clear, your package management software (in this case, aptitude) will handle that for you. You won't need to do anything in addition to the command provided.

Yes.

---

