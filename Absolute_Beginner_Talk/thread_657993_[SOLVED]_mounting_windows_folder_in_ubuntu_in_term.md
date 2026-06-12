---
title: "[SOLVED] mounting windows folder in ubuntu in terminal"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by k0debreak on 2008-01-04
Hi, I'm a new ubuntu user and i'm starting to like ubuntu. I'm using 7.10. Can someone help me on how to view the contents of a windows directory in terminal?

here's the scenario:

- I went to the terminal and typed in $ sudo mount -t ntfs /dev/hda1 /mnt
- then I did $ cd /mnt
- then $ ls

now, this showed me the contents of my c: drive like Program Files, Documents and Settings etc..suppose that I want to view the contents of Program Files in the terminal, what command should I use because I did $ cd Program Files and I received the message saying  "No such file or directory". I'm aware that I can access those folders' contents  in Nautilus but how can I access them in the terminal.

thanks

k0debreak

---

### Post by nick_h on 2008-01-04
You need to escape the space character. Use:
```
cd Program\ Files
```
or
```
cd "Program Files"
```

Tab completion is also useful - type
```
cd Program
```
and then press the tab key.

Remember that file names are case-sensitive.

---

### Post by k0debreak on 2008-01-04
nick_h, thanks, it worked! that was great! :guitar:

---

