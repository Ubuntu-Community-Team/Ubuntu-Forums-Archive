---
title: "Ubuntu Errors.!"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by m.d. on 2007-09-16
hdc error code : 0*70 sense_key: 0*03 asc : 0*11 ascq : 0*00
hdc error code : 0*70 sense_key: 0*03 asc : 0*11 ascq : 0*00
hdc error code : 0*70 sense_key: 0*03 asc : 0*11 ascq : 0*00
hdc error code : 0*70 sense_key: 0*03 asc : 0*11 ascq : 0*00
Buffer I/O error on device hdc, logical block 65346
SQUASFS error : sb_bread failed reading block 0*1f1ec
SQUASFS error : unable to read fragment cache block [7c7b3a5]
SQUASFS error : unable to read page, block 7c7299f, size 24e1

it gives this error continously after loading the boot screen . only the numbers change. what should i do?

---

### Post by peabody on 2007-09-16
This is saying there's IO errors on your secondary master.  Where is Ubuntu installed and does it boot, or do you only see this?

---

### Post by m.d. on 2007-09-16
i can not installed ubuntu yet. i booted it from ubuntu live cd and it couldnt start i only see these errors..

---

### Post by peabody on 2007-09-17
Ah, okay, this probably just means your cd image was corrupt or had a bad burn.  Try downloading and making the disk again.

---

### Post by m.d. on 2007-09-17
it is now ok.. i burned it with 4x speed but now i got another eroor..

*Setting primary keymap...
warning.pm did not return a true value at /usr/bin/ckbcomp line 20
BEGIN failed--complication aborted at /usr/bin/ckbcomp line 20.

*Preparing restricted drivers...                                                                      **[OK]**
*Starting basic networking...                                                                         **[OK]**
*Starting kernel event manager...                                                                 **[OK]**
*Loading hardware drivers...                                                                         **[OK]**

..... it continues like this and at last it says that:

*Checking file systems...
logsave: tz_file.c :344 : __tzfile_read: Assertion 'num_types -- 1' failed
Aborted                                                                                                            **[COLOR="Red"][FAIL][/COLOR]**

*File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.

*A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
Press enter for maintanence
(or type Control-D to continue): _

---

### Post by peabody on 2007-09-17
Another bad cd.  Did you check your iso image against the md5 checksums?

---

### Post by dpar on 2007-09-17
If the md5 checksum checks out ok, try a different burning program.
This one worked well for me in windows......

[http://cdburnerxp.se/](http://cdburnerxp.se/)

---

