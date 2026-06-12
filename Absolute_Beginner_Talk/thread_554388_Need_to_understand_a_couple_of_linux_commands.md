---
title: "Need to understand a couple of linux commands"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-09-18
I read in a guidewhich instructed me to to type the following commands to help azureus update onbut I would like to know what they mean.  Any help would be appreciated.

```

sudo chmod +x /usr/bin/azureus
azureus

```

```

sudo chown -R root:root /opt/azureus/

```

Thx,

VC

---

### Post by moffa on 2007-09-18
```

sudo chmod +x /usr/bin/azureus
azureus

```

that command gives executable writes to that command. It allows anyone to run the file azureus 

```

sudo chown -R root:root /opt/azureus/

```

that command changes the owner of /opt/azureus and the -R makes it recursive to any subdirectories in it, to user root in the group root

Hope that helps

---

### Post by videocheez on 2007-09-18
> **moffa said:**
> ```

sudo chmod +x /usr/bin/azureus
azureus

```

that command gives executable writes to that command. It allows anyone to run the file azureus 

```

sudo chown -R root:root /opt/azureus/

```

that command changes the owner of /opt/azureus and the -R makes it recursive to any subdirectories in it, to user root in the group root

Hope that helps


That does help.  Thanks.  After i make  the azureus updates.  What do i type  to undo those commands

Thx,

VC

---

### Post by kfrance on 2007-09-19
I'm not sure why you would want to do this but to make a file no longer executable you could say > sudo chmod -x /usr/bin/azureus

To change the ownership back you have to know who owned the files before. Do the same command except replace root with the previous owner.

---

### Post by videocheez on 2007-09-19
> **kfrance said:**
> I'm not sure why you would want to do this but to make a file no longer executable you could say 

To change the ownership back you have to know who owned the files before. Do the same command except replace root with the previous owner.

Ya me neither.  I didn't actually know that I was making the file executable.  I thought I was some how making azureus less secure.  I'm a major noob.

Thx,

VC

---

### Post by nick_h on 2007-09-19
If you want to read the manual page for a command you can use *man*.  For example:
```
man chown
```

---

