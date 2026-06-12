---
title: "Stupid beginner question #478"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-09-22
I'm trying to copy a downloaded script to my home folder.  When I mark and drag the document to that folder, I get this message:  "Error while copying to '/home:': You do not have permissions to write to this folder?"

What gives?

---

### Post by swisscow on 2007-09-22
Change the permissions of the file. Use the terminal and I believe the command is:

```
chmod a+x filename
```

then try it. It's definately something like that but I could be wrong - someone will correct me very soon I imagine!

---

### Post by Nikitas350 on 2007-09-22
Try the following "sudo cp theoriginalfileadnfolder thedestinationfolderandfile" or "sudo chmod 777 thefolderwiththewrongpermissions". I hope this helpssssss :)

---

