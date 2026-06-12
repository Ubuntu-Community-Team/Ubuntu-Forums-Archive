---
title: "flash player"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-28
I just visited circuit ----  and they had an ad that required flash player.  What do I need to add to view this stuff in edgy.


Thanks

---

### Post by dbbolton on 2006-12-28
download the flash player 9 archive, extract it, and 'sudo mv' to /usr/lib/firefox/plugins/


ps- i'll look around for the link

---

### Post by dbbolton on 2006-12-28
ok, i attatched the file. you'll have to extract the first one, and theres another archive to be extracted.

```
sudo mv 'pathto.so' '/usr/lib/firefox/plugins'
```where 'pathto.so' is probably like '~/flashplayer.tar.gz_FILES.tar.gz_FILES/flashplayer.tar.gz_FILES/flashplayer/libflashplayer.so'


i had to compress it twice to get the file size under the forums' attachment size limits.

better yet, just find that .so file, drag it to your home folder, and then do

[code]sudo mv '~/libflashplayer.so' '/usr/lib/firefox/plugins/'[/sudo]

---

### Post by ashmew2 on 2007-01-01
Thanks dbbolton!! :D i got flash working :D

---

