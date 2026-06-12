---
title: "Removing users"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by KaiAgni on 2006-10-04
So at one point in time I had removed the admin user. Not smart I know.  So a friend was able to correct the problem.  I thought that we had removed the old user and the sample user he had created.  The files are still visable on File Browser and one of them has some unfinished downloads.  I would like to remove them. Lend a hand and snicker. I don't mind.  Learning is fun!

---

### Post by croak77 on 2006-10-04
You can use userdel -r to remove the user and all files in the user's home directory if that's what your asking.

---

### Post by KaiAgni on 2006-10-04
Ok.  I tryed to use userdel -r with no result.
This is what I did.
 sudo userdel -r dan
userdel: user dan does not exist

Is it just an existing directory.

I looked at its permissions.  
It's file owner is 1002
It's file group is 1002

It also says that I not the owner so I can't changes it permissions.
I thought that if I was using the su or sudo I could change anything!
 There must be another way.  I less direct but still fuctional one.
Snicker away! I know,I don't know command prompt or code whatever you call it. Lend a hand if you can. Thanks

---

### Post by jordanmthomas on 2006-10-04
```
sudo rm -r /home/dan
```
provided /home/dan exists and providing you can use sudo.

---

### Post by KaiAgni on 2006-10-05
Thanks worked like a charm!!

---

