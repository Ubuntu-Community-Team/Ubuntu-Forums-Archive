---
title: "Ho do I move files between users?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by kfehr911 on 2007-09-10
I want to know I can keep my files on my user but also transfer some files to other users. I've started users for my kids but need to transfer certain video & movie files to there users.  Not all of them.  I'm not certain how to do it properly.  Could you please lend a helping hand. Tanks

---

### Post by bodhi.zazen on 2007-09-10
Make a shared directory and a new group.

Call the new group something like say multimedia

add appropriate family members to the group

System -> Administration -> Users and Groups -> -> Hit the Manage Groups button ....

Now,

sudo mkdir /media/mutimedia

[indent]# makes a new directory for sharing[/indent]

sudo chown root.multimedia /media/multimedia

[indent]# sets ownership on shared directories[/indent]

sudo chmod 770 /media/multimedia

[indent]# sets permissions so anyone in the multimedia group has full access[/indent]

You might also want to set the sticky bit :

sudo chmod g+s /media/multimedia

[indent]# Ah, the stick bit, this is subtle. When this is set, nwe files created in teh directory are owned by the group that ownes the directory (rather then the primary group of the user that created the file). I am not sure this will help when yiou move a file (copy, move) into the directory though, I think you will need to manually change ownership with :

sudo chown root.multimedia /media/multimedia/<file>

Or you can do that with nautilus (Open nautilus, navigate to /media/multimedia -> Right click on a file -> select properties -> click permissions tab 

You may need to open nautilus as root ```
gksu nautilus /media/multimedia
```[/indent]



Share directory : [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

---

### Post by philinux on 2007-09-10
For the uninitiated would you explain what each of those cli commands is doing

---

### Post by bodhi.zazen on 2007-09-10
> **philinux said:**
> For the uninitiated would you explain what each of those cli commands is doing

LOL

Updated my post somewhat, better now I hope :)

---

