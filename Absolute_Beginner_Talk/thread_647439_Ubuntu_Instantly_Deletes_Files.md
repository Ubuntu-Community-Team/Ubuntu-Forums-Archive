---
title: "Ubuntu Instantly Deletes Files"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by vahnx on 2007-12-22
I just installed Ubuntu 7.10 the other day, and I'm pretty new to Linux. When I delete files from my laptop hard drive they go straight to the trash, which is OK, but when I delete them from my external drive they skip the trash and are perma deleted. Is there any way I can enable a prompt for when I delete my folders/files so I don't delete them by accident (Like the Windows "Are You Sure"?

---

### Post by nowshining on 2007-12-22
if ur using ntfs, or so forth, they are not perm. deleted, it creates it's own .trash folder in the main root directory of that hd, 

in nautilus press ctrl + h, and find .trash.

---

### Post by thelatinist on 2007-12-22
Are you sure that these files are not being placed in a .Trash folder on your external hard drive?  Use nautilus to browse and see.  That's what happens on mine.

---

### Post by nowshining on 2007-12-22
oh and adding that u have to delete the item in .trash to perm. delete it or delete the .trash folder itself, don't worry the next time u delete an item it will auto re-create itself.

---

### Post by vahnx on 2007-12-22
I was doing some searching and yes I just found out they go to this trash folder. That solves my worries. Thanks guys for the input.

I was also wondering if there is a way for Ubuntu to prompt me when I delete a file from no matter where (whether it be my external or from the hard drive) saying "Are you sure you want to delete this file?",

---

### Post by nowshining on 2007-12-22
as for external no not that i know of, for internal when u go to empty the trash itself it will/should prompt u.

---

### Post by vahnx on 2007-12-22
Oh sorry, I ment when I press delete to send a file into the trash, is there a way for it to prompt me before it goes into the trash? You know, like in Windows.

---

### Post by nowshining on 2007-12-22
probably with some hacking u can or if they included that in hardy heron (dev) in that nautilus version or newer, i dunno about the hardy heron part, but maybe a script...u'll have to do that on ur own and research it or maybe i will for u, now that i think about it...

---

### Post by jken146 on 2007-12-22
Just my personal opinion, but I find that feature in Windows rather annoying, considering that there is a trash from which all my deleted files ar recoverable.  I find that many steps to delete something counter-productive.

---

### Post by thelatinist on 2007-12-22
> **jken146 said:**
> Just my personal opinion, but I find that feature in Windows rather annoying, considering that there is a trash from which all my deleted files ar recoverable.  I find that many steps to delete something counter-productive.

Hear hear!  I always turned that "feature" off in Windows.

---

### Post by nowshining on 2007-12-22
i do think it's alright for a small subset of files, or a folder/directory but a ton of them and it does get very annoying.

---

### Post by CatKiller on 2007-12-23
> **vahnx said:**
> I was also wondering if there is a way for Ubuntu to prompt me when I delete a file from no matter where (whether it be my external or from the hard drive) saying "Are you sure you want to delete this file?",

If you've got the warning when you empty the trash then you will also get a warning when you delete an item. You won't get a warning when you move an item to the trash. This is a reasonable compromise, since you get the warning at the point where you're actually doing something destructive, rather than just when you're moving your files about.

---

### Post by vahnx on 2008-01-02
I personally would find it more convenient for a prompt to appear when you press 'delete' on a file, whether it be on an external drive or on the main hard drive. That way if I accidently press delete on a file or whatever, I won't have to dig around a trash.ubuntu folder to restore it.

---

