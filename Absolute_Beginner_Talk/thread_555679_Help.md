---
title: "Help"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by MuhdHusaini on 2007-09-20
I got a problem i can't delete any file in my partition. Any way to fix it and also i can't copy file to other partition. I'm using ubuntu 7.04 .

---

### Post by Perfect Storm on 2007-09-20
Which partition are you talking about? Is it in your windows?

---

### Post by MuhdHusaini on 2007-09-23
I have del my windows i just have ubuntu all the partition i can't paste can't share can't the permission say root is the owner.

---

### Post by PmDematagoda on 2007-09-23
Keep in mind that you can only change anything within your Home folder, any place such as the "FileSystem" which hold the system files requires you to be root.

Meaning either you do the changes in Recovery mode, or go through the terminal and assume "sudo" powers and do the changes from there.

Ofcourse, Artificial Intelligence may have something better:)

---

### Post by funrider on 2007-09-23
u should learn the concept of ownership and group for linux environment first...

[http://www.linuxhelp.net/newbies/#chown](http://www.linuxhelp.net/newbies/#chown)

---

### Post by PmDematagoda on 2007-09-23
> **funrider said:**
> u should learn the concept of ownership and group for linux environment first...

[http://www.linuxhelp.net/newbies/#chown](http://www.linuxhelp.net/newbies/#chown)

A better idea funrider, but it isn't difficult to adopt to Linux's Ownership methods as I did in just a few hours of installing Linux for the first time.(But of course learning it properly never harms and just accelerates it)

---

### Post by MuhdHusaini on 2007-09-23
Is there any way that i can contorl all the partition i am the owner. Now i can't del or any thing i want to be like windows can copy and del and much more?

---

### Post by aysiu on 2007-09-23
This link will help you access system files:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

And do not *chown* or *chmod* anything. That's a quick way to render your system unusable.

---

### Post by Perfect Storm on 2007-09-23
As aysiu said don't mess with the permissions, you'll end up with a broken system. The permission is there for security reasons (amonst other things).

To cp something from one place to another;
```
sudo cp -r <file> <distination>
```

To move a file
```
sudo mv <file> <distination>
```

eg. to cp everything from a specfic folder to another
```

cd </where/your/files/are>
sudo cp -r * <distination>
```

More info 
About cp and mv (or other commands)
```
man cp
man mv
man <command>
```

explanation:
man = manual
cp = copy
mv = move
sudo = superuser do
cd = change directory

---

