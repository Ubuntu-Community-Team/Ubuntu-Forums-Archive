---
title: "VMware Server Console won't load anymore..."
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-11-18
I just ran some updates this morning on Ubuntu... tried to launch VMware Server Console and no go... a task bar with "Starting VMware Server Console" appears... lasts for about 45 seconds, then disappears.

Any ideas what's stopping it from loading?

---

### Post by djsroknrol on 2006-11-18
Try typing "vmware" in a terminal and see what messages you get....the last time I had that happen, the kernel image files were the culprit, but it could be any number of things...

---

### Post by BLTicklemonster on 2006-11-18
in a terminal:

```
cd /home/yournamegoesrighthereyouknow/vmware-server-distrib

then 

./vmware-install.pl

and follow through!
```


(if it does not install, try sudo ./vmware-install.pl)

you might want to copy that and put it somewhere safe... like pm it to yourself here.

---

### Post by molotov00 on 2008-05-29
I found this on Google and wanted to post my results also. I fixed it.

I ran vmware from command line, and was told that the GCC compiler wasn't found. I did and apt-get and ensured that I had 4.2, the version vmware said it didn't have.

I ran:```
find / -name '*libgcc*'
``` to find out where my GCC was installed. Once I knew that, I created a symlink like so:```
sudo ln -s /usr/lib/gcc/i486-linux-gnu/4.2/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```

I backed up the original libgcc_s.so.1 in the vmware directory first.

Another way would be to find vmware's config and have it point to the proper GCC libraries. 

Anyway, this worked for me. It got vmware finding the right libs and the console loaded.

Hope that helps someone! I only posted it here bc i figured Google likes to find this thread when people search for the same problem I had.

M

---

