---
title: "Invalid argument"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-07-11
I'm trying to copy my .kde/share/apps/kmail/mail folder to a USB stick. If I do it through Konqueror, the mail folder, the subfolders (inbox, sent-mail, etc) copy, and *some* of the subfolders (cur, new, tmp) copy, but none of the messages. So I tried the old-fashioned way, in the terminal
[email]user@ubuntu:~/.kde[/email]/share/apps/kmail$cp -r mail /media/sda1
and got a whole bunch of invalid argument errors, e.g. 

cp: cannot create regular file `/media/sda1/mail/Peter 2005/cur/1140619746.7261.TECgE:2,S': Invalid argument

Please help. I'm trying to move my files to a new computer.

---

### Post by Paerez on 2006-07-11
You can always zip it up. So do this:
```
# tar cjf /media/sda1/mail_backup.tar.bz2 ~/.kde/share/apps/kmail/mail
```

Then you have one zipped file on the flash disk. Then, on the next computer (if its linux) you can do:
```
# tar xjf /media/sda/mail_backup.tar.bz2 -C /where/it/goes/to
```

If you are moving it to a windows comp, I can help you use the zip command to make a zip file.

---

### Post by editrix on 2006-07-11
Woo-hoo! It worked! Thanks so much, Paerez!

> **Paerez said:**
> 

If you are moving it to a windows comp, I can help you use the zip command to make a zip file.

Nope, thanks, I'm really trying to avoid ever using Windows when I'm online :-)

Again, thanks so much.

---

