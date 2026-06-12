---
title: "File name format in rc2.d"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by One_of_Six on 2007-06-25
I have just created a symlink from a startup script file in init.d to rc2.d The new symlink file appears in rcd.2 with the correct file name "RunEchoLink"

However, in my rc2.d file, all the other files are single words preceded by an upper case "S" and a number between 1 & 99 e.g. S20samba, S20vftp, S91apache etc. I don't know what the prefix is all about - perhaps a priority or order of execution? if so what "Snumber" do I need for my RunEchoLink symlink?

---

### Post by hartz on 2007-06-25
The script which runs the programs in rc2.d (and all the other rc?.d directories) runs only scripts which starts with a capital S.

It also, by design, runs them in the order which they show when you run "ls" in this directory, so give your script a number making sure that it will come after everything else which it depends on.

---

