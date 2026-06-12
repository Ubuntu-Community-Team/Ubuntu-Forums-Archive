---
title: "Disk clean up"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by DodgyP on 2006-12-02
Hi all,

This is probably simple..... but i can't figure it out. I store back up files from a windows computer on a second hard drive on my Linux system. Just as a security measure in case the windows computer does what they do best and goes blue screen gets a virus etc etc. So the second hard drive mounted with fstab as /backup gets a lot of stuff copied to it then occasionally deleted and then lots of stuff copied again.

When I delete the old back up files the disk still shows up as being 70% full .

If I try to copy my new backup files I'm told there is not enough room??? So ultimatly I format the disk and then copy the files.

Is there a way to delete the files and free up the space without a format??

Thanks

DodgyP

---

### Post by 56phil on 2006-12-02
This may be a really silly question: How do you delete the old files?

---

### Post by Chinkostu on 2006-12-02
are you emptying the trash can? :)

edit: ```
sudo rm [filename]
```

for files

```
sudo rmdir [directory name(must be empty)]
```

Removes folder(s)


is how i do it. are you doing it right?

---

### Post by DodgyP on 2006-12-02
Ok usually, I just delete in gui,highlite and right click move to garbage bin , nothing shows up in the trash so can't empty it?? I just move to trash the files appear gone but the disk space is still used and the bins empty.

Should I use a an rd command in terminal??

DodgyP

---

### Post by 56phil on 2006-12-02
OK, put everything you want to delete in a folder. Then, from a terminal```
rm -r <folder name>
``` The -r stands for recurse. It will delete the folder and everything in it. Good luck and come back if you have any questions.

---

### Post by CatKiller on 2006-12-03
> **DodgyP said:**
> Ok usually, I just delete in gui,highlite and right click move to garbage bin , nothing shows up in the trash so can't empty it?? I just move to trash the files appear gone but the disk space is still used and the bins empty.

You'll probably find that on that partition there is a hidden directory (Ctrl-H to show hidden files) called .Trash-username. You can remove the files from there to get the space back.

---

