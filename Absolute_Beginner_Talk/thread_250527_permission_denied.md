---
title: "permission denied?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by hc2995 on 2006-09-04
ok when i try to use $ make install for apache i get "permission denied" i thought i was the highest owner and had all permission since im the only person on this system? Is there a way to give me all permissions so that i can do as i wish?

---

### Post by Scorpuk on 2006-09-04
```
sudo su
```


This will switch you to the superuser (root) and give you permission to do anythign on your computer. Include breaking it :eek:

---

### Post by meborc on 2006-09-04
since make install will need to edit/create files with permissions above normal user, use: 
```
sudo make install
```

---

### Post by petri on 2006-09-04
I think you are not the "highest owner". The root is 8) 

So you just need to use sudo ;)

---

### Post by hc2995 on 2006-09-04
ok i used the sudo su and got that working but is there a way to make me the highest user?

---

### Post by Anonii on 2006-09-04
> **hc2995 said:**
> ok when i try to use $ make install for apache i get "permission denied" i thought i was the highest owner and had all permission since im the only person on this system? Is there a way to give me all permissions so that i can do as i wish?
Read this for full instructions and details on what root is and what sudo is:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by navneeth on 2006-09-04
While we are on the topic of permissions...I was extracting a css file into the Firefox profile folder. While doing so, I got this message -

Extraction not performed

You don't have the right permissions to extract archives in the folder "/etc/firefox/profile/chrome"

Will sudo su help?

Thanks

---

### Post by Anonii on 2006-09-04
Of course it would, but you need some "mv" or "cp" commands which you should learn. Execute from the console  _man mv_ and _man cp_ for more info on how to use the move and the copy command from the console :)
Another way would be to try: **_gksudo nautilus_** to open Nautilus as the root and copy-paste with it. *But be careful and close it IMMEDIATLY after you perform your task, leaving any application open as root is evil.*

---

### Post by Scorpuk on 2006-09-04
One thing to remember when using sudo su is that any file or folder created while logged in as the superuser will be read only from your normal user (if in your home folder)

I have created folders on my home desktop while still logged in as superuser and couldn't copy or move them later as I didn't have the right user privilages.


It's tricky, but I think the security of not being able to crash the computer with incorrect commands is an advantage.

---

### Post by monktbd on 2006-09-04
> **Scorpuk said:**
> I have created folders on my home desktop while still logged in as superuser and couldn't copy or move them later as I didn't have the right user privilages.


well there is the option to change the owner and the group of file as well.

> sudo chown myuser:mygroup myfile

will do that.
usually the use joe has also the group joe, so
> sudo chown joe :joe joesfile

would change the user and the group to joes default settings.
be careful to not change permissions delibaretly outside of the home folder. it might mess up the whole system.

---

