---
title: "Hcid.conf"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-08-28
I need to edit this file to change a pin number from 1234 to 0000.  When I try to save the new file it says its READ only and I don't have permission.  How can I change this file?

---

### Post by tyggna1 on 2007-08-29
type in
```

sudo gedit /path/of/file/Hcid.conf
```

That will give you the permissions you need.

Also it'd be a good idea to back up the file, to do so, type in:
```
sudo cp /path/of/file/Hcid.conf /path/of/file/Hcid.conf.backup
```

before you edit a .conf file--that way, you can type in 
```
sudo cp /path/of/file/Hcid.conf.backup /path/of/file/Hcid.conf
```
if things get totally screwed up.  You can access the command prompt--even when things won't boot regularly by pressing ctrl-alt-F1 anytime.

---

