---
title: "best way to copy files to another account?"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by ezphilosophy on 2006-12-25
I'm always a big advocate of searching for the answers before you ask them (as most of the time they have already been answered).
I've done a few searches but I know that with this kind of question + my Ubuntu community, the question can be answered much more efficiently by just making the post.

What is the easiest/most convenient way to copy files to another account on Ubuntu?

If I'm in my account (home folder) and I want to copy a file to my wife's account (home folder), how can I do that?  

If you just use the "cp" command, it will tell you "permission denied".  If I use "sudo", the permissions/ownership will be "root" and therefore access will be denied.  If I go to her account and use "sudo chown [user] [file]", that also doesn't work, moreover, even if it did work, would be a bit troublesome.

Is there a more complete command I can type in the terminal that will copy the file over to her account AND give her ownership/permissions?

Any help is greatly appreciated!

---

### Post by taurus on 2006-12-25
Okay, assuming your login name is husband and her login name is wife and you want to copy picture to her account, open a terminal and do

```
sudo cp picture /home/wife
sudo chown wife:wife /home/wife/picture
```

Otherwise, have her login to her account and copy stuff from your account to her own account...

---

### Post by ezphilosophy on 2006-12-26
Perfect!  Thanks much Taurus!

---

