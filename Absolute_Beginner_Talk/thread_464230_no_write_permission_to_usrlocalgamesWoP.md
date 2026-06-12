---
title: "no write permission to /usr/local/games/WoP"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Grundalizer on 2007-06-04
i am trying to install world of padman and after i go through everything this    /usr/local/games/WoP comes up and says input install path, it keeps saying i do not have persmission, alternative or solution ?

pls n thanks

---

### Post by jonward0690 on 2007-06-04
Well you could log in as root and change this.

---

### Post by Grundalizer on 2007-06-04
how do you do that? and then go about the same process as before? will i have to rerun the .run file?

---

### Post by Grundalizer on 2007-06-04
well i changed the path to /home/god/usr/local/games/WoP and it worked, i chose to not install symbolic links in some /bin area.

---

### Post by ncappel1 on 2007-06-04
Sounds like it's just a permissions, issue. Are you sure that users other than root can read/write/run the file? You may want to change the permissions on it so you don't have to log in as root (which in general is not reccomended).

---

### Post by pjman on 2007-10-01
I got the same error. The 'bin' directory needed to be created.

```
sudo mkdir /usr/local/bin
```

Then run:

```
sudo ./worldofpadman.run
```

---

