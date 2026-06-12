---
title: "Referring  to a Remote Machine in Terminal"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by mattice06082 on 2006-09-19
I was able to set up a Samba share between the Ubuntu machine and two XP machines on my home network by following [http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605").

After following the HOWTO I'm able to see my windows machines using the Places -> Network Server browser.  However is there a way to refer to the network machines from within the Terminal?  I've tried
```
ls //MachineName/SharedDir
ls \\MachineName\SharedDir
ls //privateipaddress/SharedDir

```but haven't had any success.  I don't know if I need to "mount" the samba shared machines as devices or if I just don't have the syntax correct.

Thanks

smbmount is what I was looking for.  Found it at [http://www.ubuntuforums.org/showthread.php?t=255872]("http://www.ubuntuforums.org/showthread.php?t=255872").

---

