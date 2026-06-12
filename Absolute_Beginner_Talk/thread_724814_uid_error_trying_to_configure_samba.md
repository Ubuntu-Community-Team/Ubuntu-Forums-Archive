---
title: "uid error trying to configure samba"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2008-03-15
using kubuntu 7.10. I had samba file sharing working, but then I borked my OS and ended up doing a re-install while keeping my /home partition. When I run the samba conf command I get the following error:

```
dragon@smaug:~$ sudo kate /etc/samba/smb.conf
[sudo] password for dragon:
Error: "/var/tmp/kdecache-dragon" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dragon" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-dragon" is owned by uid 1000 instead of uid 0.
```

Does this mean that I need to change ownership of the home partition? The conf command does open the samba conf file in a text editor. I will go ahead and configure samba in the editor, but I think it may not work due to the errors. Any ideas or comments? I will re-visit this thread in a bit with more info. Thanks

---

### Post by paydaydaddy on 2008-03-15
Been at this for a while, but so far I haven't gotten to where I can share files with other computers on the network. I can see windows shares on kubuntu, but no kubuntu shares on windows. I will endeavor to persevere.

---

