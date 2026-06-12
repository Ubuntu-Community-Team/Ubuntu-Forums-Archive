---
title: "Reinstalled OSX, boot choice gone"
date: 2006-10-11
forum: Apple PPC Users
---

### Post by seedy on 2006-10-11
How do I get the bootloader choice back? I still have the Previous Systems folder.

Thanks.

---

### Post by 3rdalbum on 2006-10-11
Enter OpenFirmware by holding down Command-Option-O-F on startup.

At the prompt, type:

```
boot hd:x,yaboot
```

(substitute x for the partition number that the bootloader resides on - if you don't know, just try numbers from 0 upwards)

When you get it right, the bootloader will appear, and you can boot Ubuntu as normal. When Ubuntu loads, open a terminal and type "ybin". This will reinstall Yaboot.

---

### Post by seedy on 2006-10-12
Thank you 3rdalbum. 

I might add a step, which is that when the bootloader started for me it did not give me choices. Typing help gave me the hint I needed, which was that I needed to type Linux and hit Return.

Opened Konsole and typed ybin, got a Permission denied, using sudo ybin appeared to work.

Will find out next reboot...

Edit: It works now, and thank you again for your help.

---

