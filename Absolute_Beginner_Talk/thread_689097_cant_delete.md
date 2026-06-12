---
title: "cant delete"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-02-06
I am trying to delete something off my desktop and it says:
```
Cannot move "/home/sirfon...ifi-0.9.3.2" to the trash because you do not have permissions to change it or its parent folder
```

so I went into my terminal and tried sudo rmdir -r filename

and it says this
```
rmdir: madwifi-0.9.3.2/: Directory not empty
sirfonners@sirfonners-laptop:~/Desktop$ 

```

how the hell do i get rid of this thing?

---

### Post by fiddledd on 2008-02-06
I've no idea what that folder is/does so I would say don't delete it unless you are sure. However if you need to check the folder contents and delete it just run Nautilus as root Alt+F2 then gksudo nautilus
Then you have permission to delete etc.

---

### Post by njparton on 2008-02-06
Try the following:

```
sudo rm -fr *
```

be warned though that it will delete _EVERYTHING_ at that level and below.

---

### Post by sirfonners on 2008-02-06
> **fiddledd said:**
> I've no idea what that folder is/does so I would say don't delete it unless you are sure. However if you need to check the folder contents and delete it just run Nautilus as root Alt+F2 then gksudo nautilus
Then you have permission to delete etc.

its just a madwifi extraction that i installed, but didnt work.
I ended up installing the windows drivers using ndswiper or whatever it is lol
so i dont need the madwifi thing so I think its cool

---

### Post by oedha on 2008-02-06
how if rm -rf ?
or change that folder permission first before remove
sudo chmod -Rf 777 /foldername

---

### Post by hyper_ch on 2008-02-06
First try:

```

rm -Rf /path/to/madwifi-0.9.3.2

```

if that gives errors about privileges, then use:

```

sudo rm -Rf /path/to/madwifi-0.9.3.2

```

---

