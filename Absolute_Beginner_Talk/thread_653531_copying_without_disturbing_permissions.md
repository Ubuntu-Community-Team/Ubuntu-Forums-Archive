---
title: "copying without disturbing permissions?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Blessed_Coffee on 2007-12-30
I was wondering if it is possible to copy files/folders without changing their original permissions and set owner.  The files belong to many different users on the system including their .dmrc file in their home directory.  It would be very helpful if I didn't have to copy the files logged in as each user.

---

### Post by bhold on 2007-12-30
cp command with -p option. From a terminal, type man cp for details.

---

### Post by aidanr on 2007-12-30
The cp command has a -p or --preserve arguement that will do that, but only as root for security reasons.

Edit: too slow :)

---

### Post by eternicode on 2007-12-30
I believe that this is defauilt behavior for most opying methods in linux.

Try ```
cp -p <etc, etc>
```

```
-p     same as --preserve=mode,ownership,timestamps

       --preserve[=ATTR_LIST]
              preserve  the  specified  attributes  (default:  mode,ownership,timestamps)  and  security contexts, if possible additional
              attributes: links, all
```

Or you could go with the even more encompassing "-a"

```
-a, --archive
              same as -dpR
```

---

