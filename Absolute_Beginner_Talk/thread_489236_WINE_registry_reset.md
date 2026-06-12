---
title: "WINE registry reset"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by bobabot1 on 2007-07-01
(Please move this if it's in the wrong section. My apologies)

I accidentally copied a .reg file into my WINE registry trying to make Starcraft work. Now, whenever I run SC, it just spins the CD a little then closes. Is there any way to completely reset my registry? I've uninstalled multiple times but it doesn't seem to work.

---

### Post by cleverselfreferentialname on 2007-07-05
Reinstalling won't work because it doesn't purge the config files. Those are in your home directory, in a "hidden" folder, .wine.

---

### Post by cleverselfreferentialname on 2007-07-05
'rm -rf .wine' will do what you want it to, but it will also remove your SC install.

---

### Post by moredhel on 2007-07-05
so uninstall wine, delete the folder .wine, then reinstall ;)

EDIT: or the idea above ^ :P

---

### Post by dfreer on 2007-07-05
You could also just copy your starcraft program files out, then rm .wine. Although if the problem lies in your starcraft install and not wine then you'll have to reinstall it anyways.

---

