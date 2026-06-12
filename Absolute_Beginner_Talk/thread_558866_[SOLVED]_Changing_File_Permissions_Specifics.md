---
title: "[SOLVED] Changing File Permissions Specifics"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by FrozenFlame22 on 2007-09-24
I've got a rather specific question regarding file permissions, and I've not been able to find out what I need to do on my own. I need to change file permissions on a very large group of files. There are over 4000 files in nested folders occupying a space of about 5 GB. All of these files are already owned by me.

I need to change them to being modifiable by everyone in the group "parents", of which I am a member, and read only for all others. They should remain owned by me. I also need to do this through the terminal, since the nautilus folder options are not applying to enclosed folders.

---

### Post by vikram on 2007-09-24
chmod 774 -R FOLDERBNAME

see this for more details
[https://help.ubuntu.com/community/FilePermissions?highlight=%28permission%29](https://help.ubuntu.com/community/FilePermissions?highlight=%28permission%29)

---

### Post by FrozenFlame22 on 2007-09-24
Thanks for the quick reply and for the very informative link!

I neglected to mention that "parents" is not my primary group. I can see how the above command would work, but how would I specify the "parents" group?

---

### Post by FrozenFlame22 on 2007-09-24
*Bump*

---

### Post by mendingo84 on 2007-09-24
since you are in the group "parents", the second 7 on the 7**7**4 number means that everyone in your group cand "read, write and execute" those files

---

### Post by Dr Small on 2007-09-24
```
chmod 474 -R FOLDERNAME
```

474 means this:

Owner: Read
Group: Read, Write, Execute
Others: Read

Here is how I calculated it, because my skills on memorizing chmod permissions are somewhat slacked:
[http://www.classical-webdesigns.co.uk/resources/whatchmod.html](http://www.classical-webdesigns.co.uk/resources/whatchmod.html)

Dr Small

---

### Post by FrozenFlame22 on 2007-09-24
I just tried it and it applied the group "frozenflame" instead of the group "parents." Here's exactly what I typed:

chmod 774 -R /media/thorin/Music

---

### Post by Dr Small on 2007-09-24
Maybe you need to do some reading on changing groups ?
```
man chgrp
```

---

### Post by mendingo84 on 2007-09-24
well then, change the owners of that files. type this:

```
chown -R youruser:parents /path/to/directory
```

---

### Post by FrozenFlame22 on 2007-09-24
Nifty link Dr Small! I'm definately going to bookmark that! I'll still need "774" because I'll need to be able to write and execute as well. ;) My problem seems to be applying the correct group. I'm part of several groups and it's just taking the first one.

---

### Post by Dr Small on 2007-09-24
```
chgrp -R frozenflame:parents /media/thorin/Music
```

---

### Post by FrozenFlame22 on 2007-09-24
Changing owners worked! Thanks for the help!

---

### Post by mendingo84 on 2007-09-24
enjoy ;)

---

### Post by Dr Small on 2007-09-24
Please remember to mark threads as "SOLVED" from Thread Tools, if the thread is solved ;)

---

