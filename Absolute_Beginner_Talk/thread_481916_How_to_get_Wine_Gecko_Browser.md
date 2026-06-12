---
title: "How to get Wine Gecko Browser"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by bamesah on 2007-06-23
Hi,

When i try to download Gecko Browser from Wine, it just says Downloading and doesn't download anything,

Is there a way to download it manually??

---

### Post by bamesah on 2007-06-23
any ideas?

---

### Post by bamesah on 2007-06-23
any ideas??

---

### Post by bamesah on 2007-06-26
any ideas?

---

### Post by bamesah on 2007-07-05
any ideas

---

### Post by moredhel on 2007-07-05
I know there is, wait while i find it ;)

---

### Post by moredhel on 2007-07-05
If the Gecko engine doesn't download (servers are down) then download [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269) to the "/tmp" directory and point Wine to it (save this as-is to the "/tmp/file.reg" then import with command 'regedit /tmp/file.reg':

```
[HKEY_CURRENT_USER\Software\Wine\MSHTML]
"GeckoUrl"="z:\\tmp\\wine_gecko.cab"
```

---

### Post by bamesah on 2007-07-07
Thanks, That Worked

---

