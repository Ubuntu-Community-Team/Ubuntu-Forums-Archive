---
title: "System &gt; Administration &gt; Disks?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by fobnicat on 2007-04-06
When i follow the path System > Administration > Disks.... Disks isnt there.. I had not noticed this until I was reading the Ubuntu.com manual for 6.10  Any ideas??

---

### Post by caffienefree on 2007-04-06
I'm not entirely sure. Where is this in the documentation?

If you want to see a list of partitions, you can do:

sudo parted
print all

---

### Post by fobnicat on 2007-04-06
here is where i read it:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/other-hardware.html#listpartitiontables](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/other-hardware.html#listpartitiontables)

---

### Post by caffienefree on 2007-04-06
I may be wrong, but I think that was a tool from dapper that was removed from edgy?

Try sudo apt-get install pysdm.

---

