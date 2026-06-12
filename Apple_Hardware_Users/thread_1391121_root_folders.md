---
title: "root folders"
date: 2010-01-26
forum: Apple Hardware Users
---

### Post by Tycho59 on 2010-01-26
I have a bunch of empty root owned folders that were created while trying to setup my built in isight camera.  I want to delete these folders.  How do I do this?

---

### Post by doas777 on 2010-01-26
just a caution, you may not want to, if the software installed correctly, as it may expect them in future. also you want to make absolutely sure that those folders did originate with your install.

you can delete them in the gui by hitting Alt + F2 and entering
```
gksu nautilus
```. it will prompt you for your passwd and then open a file manager window. be very careful witht ath window as it can delete anything.

or if you want to use the cli, open a terminal and enter
```
sudo rmdir <path to folder>
```

---

### Post by chiefsittingduck on 2010-01-26
Hit "Alt-f2" and check "run in terminal", then type "sudo nautilus" , then you will be asked for your password.
After that you will be greeted by a file-manager with root accesss..

---

