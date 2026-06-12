---
title: "having troubles getting to directories via terminal"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-12
ok, i am noob, and don't understand how to access a directory through the terminal, lets say i want to get there using CD

i typed in cd /home/admin/Savage/ and it told me that "no such file or directoy" am i doing this right?

---

### Post by meborc on 2006-09-12
try to go step by step

```
cd /home
cd admin
cd Savage
```

or to make sure you have no typo-s
```

cd /ho [hit TAB key for auto-complete]
cd ad [TAB]
cd Sa [TAB]
```

and use ls inside a directory to see if the dir you need is really there
```
cd /home
ls
```
you should see admin now

---

### Post by Najand on 2006-09-12
Hmm, I don't know your directory name... Use 
```

ls

```
to see what is in your directory... then cd the directories (dark blue ones) there..

---

### Post by g4me0ver on 2006-09-12
Just Remember Linux is case Sensitive...;)  and you should use auto-complete [tab key] ... good luck,

---

### Post by bodhi.zazen on 2006-09-12
cd is correct. It sounds as if the directory does not exit.

Try also:

pwd = Print wroking directory.

ls = "list". Will list all files/directories.

mkdir <name of dir> = make directory of the given name.

Linux is case sensative.

See also:

[Linux commands](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

