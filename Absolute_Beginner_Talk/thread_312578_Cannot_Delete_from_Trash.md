---
title: "Cannot Delete from Trash"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-04
I have 2 folders that I moved to Trash after an unsuccessful attempt to install ivtv (taht's another story)

Folder are
[LIST]
[*]ivtv0.4-0.4.8
[*]IVTV_Temp
[/LIST]


When I go to the trash and try to delete either folder, I get the following error.

Error while deleting.
"/home/decl...x-init.mpg" cannot be deleted because you do not have permissions to modify its parent folder.

Any ideas on why I can't delete these and how I could reslove the issue?


Thanks

---

### Post by taurus on 2006-12-04
Look at the ownership of those files!  Make sure you are the owner and not root or somebody else.  Otherwise, you have to remove them using the sudo command...

---

### Post by bruenig on 2006-12-04
sudo rm filename

---

### Post by dkenny on 2006-12-04
What is the full path for trash?

---

### Post by echo $USER on 2006-12-04
/home/your.user.name/.trash

---

### Post by dkenny on 2006-12-04
Hmmm.
I can't seem to see the trash folder, maybe this is the issue?

declan@main-desktop:~$ cd /home
declan@main-desktop:/home$ cd declan
declan@main-desktop:~$ cd trash
bash: cd: trash: No such file or directory
declan@main-desktop:~$ dir
Desktop  Documents  Shared\ Documents
declan@main-desktop:~$

---

### Post by kakalaky on 2006-12-04
```
cd ~/.Trash
```

---

### Post by dkenny on 2006-12-04
Got it, Thanks guys.

---

