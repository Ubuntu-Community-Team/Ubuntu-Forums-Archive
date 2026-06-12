---
title: "[SOLVED] Installation of program"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by a0peter on 2007-10-11
Can someone help me with installing a small program called Tagore on Gutsy. Cant find any makefile and dont know what to do?

It can be found here:
[Tagore]("http://www.dospeixos.net/projects/tagore/")

---

### Post by mali2297 on 2007-10-11
Open terminal, go to the extracted directory and type
```

./tagore.rb

```
If it doesn't work, you may need to install some dependencies.

---

### Post by a0peter on 2007-10-11
Thank you! :KS

Had to fix some dependencies: '
> sudo apt-get install libglade2.0-ruby ruby libgtk-mozembed-ruby libgtk-trayicon-ruby

---

