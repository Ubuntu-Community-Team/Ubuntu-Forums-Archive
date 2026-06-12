---
title: "Permissions to write to a folder or drive using file manager"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by exomanila on 2007-07-01
How do I get permissions to write to a folder or drive using file manager. It always gives me I do not have permission. I cant find anything on the administrative menu to modify this. Please help thanks:(

---

### Post by phizikal on 2007-07-01
Open up shell:

```

sudo chown USRRNAME /folder/folder

```

Replace your username with yours and put /folder/folder as whatever folder you want to get permissions for.

---

### Post by mcduck on 2007-07-01
You should not change permissions of any file or directory outside your home. They have certain permissions for a reason and changing them might result in broken system.

Instead, when you need to put files in system directories you can press alt-f2 and run 'gksudo nautilus' to open the file manager as root.

---

### Post by JohnnyC44 on 2007-07-03
Thanks here, folks!  I was having a permissions issue myself, which is why I ended up at these posts.  Mcduck, your instructions for opening the file manager as root to allow me to copy a folder into a root folder worked like a charm.  John

---

