---
title: "Fatal error upon running updatedb (with sudo)"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-07-16
Hello, everyone.

I I am having a problem when trying to run:

```

sudo updatedb

```

Upon running this command, I receive teh following error:

```

updatedb: fatal error: The temp file '/var/lib/slocate/slocate.db.stf' already exists and does not appear to be a valid slocate database. Please remove before creating the database.

```

Does anyone know how to resolve this?

Thanks very much for any help on this one.

Take care.

PS:  I am running a full installation of Ubuntu 7.04.

---

### Post by Maxtorm on 2007-07-16
Try this:
```
sudo rm /var/lib/slocate/slocate.db.stf
```
then run updatedb again.  The above command removes the offending file.

---

### Post by RKCole on 2007-07-17
Thank you, Maxtorm.  That solved my problem.  That's weird, though.  Any idea why this happened?

I had thought of removing the file mentioned, but I was afraid that I'd mess something up.

Thanks again.

Marking as solved.

---

### Post by Maxtorm on 2007-07-17
Can't say for certain, but perhaps the previous update of the locate database was abnormally interrupted?

---

### Post by RKCole on 2007-07-17
That very well could be.

In any case, thank you, Maxtorm.

---

