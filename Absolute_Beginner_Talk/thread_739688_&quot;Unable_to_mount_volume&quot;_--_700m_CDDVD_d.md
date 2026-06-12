---
title: "&quot;Unable to mount volume&quot; -- 700m CD/DVD drive not working on v7.10"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by itch808 on 2008-03-30
When I insert a CD/DVD into my Dell Inspiron 700m laptop I get the message "Unable to mount volume" and when I click on details it shows:

"mount: mount point /media/cdrom0 does not exist"

---

### Post by c-ron on 2008-03-30
From the terminal, make a directory in /media called cdrom0:
```
sudo mkdir /media/cdrom0
```

Next, create a symbolic link to /media/cdrom0 called /media/cdrom:
```
sudo ln -s /media/cdrom0 /media/cdrom
```

Then, mount the cd:
```
mount /media/cdrom0
```

Hope this helps!

---

