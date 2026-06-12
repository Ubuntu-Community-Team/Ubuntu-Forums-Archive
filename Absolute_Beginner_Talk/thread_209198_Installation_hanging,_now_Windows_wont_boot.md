---
title: "Installation hanging, now Windows wont boot"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by sweeper on 2006-07-04
I have run the Recovery console and done fixmbr and fixboot,  this does not work. I know Windows is on there, is there anything other than fixmbr and fixboot I can try?

---

### Post by catlett on 2006-07-04
Isn't there a recovery option that lets you get into system restore? Boot again and pay attention to the prompts. I think there is an option to fix installation or something like that.
Also did you get to the C:\ and enter fixboot and then fixmbr. Fixboot needs to be done first. Fixboot fixes the boot sector and fixmbr repairs the mbr on the fixed boot sector. If you did it the other way it might be worth a shot to run it again with fixboot first.

---

### Post by sweeper on 2006-07-04
Don't think I can get into system restore, I am repairing Windows now and can't get out of it, however I am sure I did fixmbr first. Thanks, that should fix it.

---

### Post by sweeper on 2006-07-04
I have just tried fixboot and fixmbr but I now get 'NTLDR is missing'?
Fixboot and fixmbr usually fix that but it is not.
I really need to get access to that Windows partition :(

edit
I deleted the partitions I made trying to install Ubuntuand created another partition and it works now. Thanks :)

---

### Post by molly_001 on 2006-07-04
Although it doesn't look really good for you, try to boot into Windows using the GAG boot manager.  It can often boot into Windows even when all else has failed.  Of course, this would be a temporary thing, if it works.  Boot into Windows and copy your data files to something else immediately.
[http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

---

