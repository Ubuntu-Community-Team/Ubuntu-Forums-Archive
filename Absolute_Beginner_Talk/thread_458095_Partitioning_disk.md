---
title: "Partitioning disk"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by muddler on 2007-05-29
My disk has only one partition. 60G on a Toshiba Satellite M35.
I am doing some collaborative work with my daughtere and granddaughter. As an octogenarian, but a realist, the work may not be finished before my demise.
How can I add a partition exclusively for that work while keeping the rest of my hard drive private. Can I set two password protected partitions?
I have an idea it can be done, but I don't know how. And will I lose any data? I'm a new noob so I hope any suggestions will be specific.
Thanks in advance.

---

### Post by smoker on 2007-05-29
is this a linux drive? the easiest way in my opinion to resize, create, and format partitions is by using the 'gparted live-cd'  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

if it is a windows partition, please use drive cleaner and defrag a few times to compact data to the start of the drive (makes it easier for the resizer).

always, though it may be a rare event, backup all your crucial data before partitioning,

i am not sure about password protecting a partition, i am sure it can be done, and there is always encryting a partition, though maybe someone who uses these means can comment better than me,

best of luck

---

### Post by seetho on 2007-05-29
I assume that you are using the entire (one) partition for Ubuntu and you need to share your notebook with your daugther and granddaugther - correct?

If so, this is not so difficult.  You just create new user accounts for them individually (with their individual passwords of course).  Each of you will have a different home directory.  By default these home directories can be read by other users so your files are visible.  You (and they) can easily change the permission of the home directory so that it becomes inaccessible to anyone else.

If you need to have a common share directory to hold common files then you can create a separate directory and change the permission so that everyone has read and write access to it.

If this scheme works for you then let me know and I can give you more detailed instructions on how to do it, unless someone else here  can offer you a better solution.

---

### Post by hillbilly on 2007-05-29
I agree with seetho. In my opinion, creating partitions for this activity would be an un-necessary overhead. Creating a different account would be ideal me thinks. 

    For e.g. you could create a new account with user id say *Admin* and set the group to *Project*. And now what you need to do is add the personal id's of your granddaughter, daughter and yourself to the group *Project*. 
    So now you can create your own directory structure by logging in as *Admin* (Ideally only one of you should have access to this id.) And make sure that whatever directory or fie you create, make sure the permission bits are set such that anyone in the group can modify and read the same. For e.g. if you are logged in as Admin and create a directory as *dir1 * then the permission bits of *dir1* should looke like this *drwxrwx---*.

---

### Post by seetho on 2007-05-29
> make sure the permission bits are set such that anyone in the group can modify and read the same. For e.g. if you are logged in as Admin and create a directory as dir1  then the permission bits of dir1 should looke like this drwxrwx---

To be able to share files, I think having umask=007 will do the trick. No?

---

### Post by hillbilly on 2007-05-29
yeah, umask=007 would do it ! That way the system would take care of setting the permissions you want, whenever you create a file or directory !!

---

