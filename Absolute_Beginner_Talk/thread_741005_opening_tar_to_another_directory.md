---
title: "opening tar to another directory"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by original_jamingrit on 2008-03-31
drop the z.  Your command should be ```
tar xvf file.tar /home/user2/openedFiles
```

tar xzvf is for *.tar.gz file extensions.  tar.gz and tar are (loosely speaking) two different compression types.  tar is an archiving format and not really compressed, .tar.gz is a compressed archive.

---

### Post by stchman on 2008-03-31
> **Auston said:**
> hi everyone..
in /home/user1 there is a file.tar ..and i want to extract it to /home/user2/openedFiles...

i thought syntax should be

tar xvzf file.tar /home/user2/openedFiles

but there is something missing i guess, it doesn't work..can anyone help?

You need to use the -C option.

```
sudo tar -C /home/user2/openedFiles -zxvf /home/user1/file.tar
```

You need to sudo since you are going from one users folder to another.  By default one user cannot modify another user's folders.

---

