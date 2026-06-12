---
title: "multi user account security?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-10-05
So when I installed Ubuntu for the first time I created this user account
[LIST]
[*]user1
[/LIST]
then I created a secondary account which seemed to belong to less groups and privileges. 
[LIST]
[*]user2
[/LIST]
> 

$ **id user1**
uid=1001(user1) gid=1001(user1) groups=1001(user1),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),104(scanner),117(admin),119(fuse)

$** id user2**
uid=1002(user2) gid=1002(user2) groups=1002(user2)


Seeing this difference I naively believed that user1 was safe from the curiosity of user2.
But when I login as user2 I can practically do this
$ cd /home
$ ls -l
$ cd user1
$ cp secret_file /home/user2
choose the user account I'm interested in and copy any files that I'm interested in to my own user account space and then check out other peoples files.  Is this normal?
If not how do I make user2 not have this power?

---

### Post by Dr Small on 2007-10-05
```
man rbash
```

---

