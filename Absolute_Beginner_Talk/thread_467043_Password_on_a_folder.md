---
title: "Password on a folder?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by stratty96 on 2007-06-07
Can I put a password on a single folder or will I have to run an encryption program??

---

### Post by AZzKikR on 2007-06-07
I don't really know why you want this, but instead of passwording a folder you can change the permissions access to that folder. Perhaps this this is a solution to what you want?

---

### Post by Inxsible on 2007-06-07
```
 
sudo chmod -R go-rwx the_folder_you_want_to_protect

```
 
Anyone but you will not be able to cd into the folder and will not be able to read or write to the folder.

---

### Post by Inxsible on 2007-06-07
To allow access to everyone again
```
 
sudo chmod -R ugo+rwx the_folder_you_want_to_protect

```

---

### Post by Regel on 2007-06-07
Or use TrueCrypt like everyone else.

---

