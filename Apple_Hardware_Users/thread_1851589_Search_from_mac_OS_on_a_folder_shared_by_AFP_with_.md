---
title: "Search from mac OS on a folder shared by AFP with netatalk+avahi on UBUNTU 10.04"
date: 2011-09-28
forum: Apple Hardware Users
---

### Post by krusto on 2011-09-28
Hi everyone,
I try to install a file server for MACS on my network using the AFP on Ubuntu 10.04.
I followed that guide [http://goo.gl/Q5WQ]("http://goo.gl/Q5WQ") only from the point "2. Configure Netatalk" to point "5. Configure Avahi and advertise services" because don't need a volume for Time Machine and i know that Ubuntu 10.04 contains netatalk 2.0.5 and I installed it using the comand:

```
sudo apt-get install netatalk
```

and editing the file /etc/netatalk/afpd.conf by deleting the last row and pasting this:

```
- -transall -uamlist uams_clrtxt.so,uams_dhx2.so -nosavepassword
```

All works well, i created a share for testing and from Lion OS i'm able to copy, paste and delete file and folders, from any users.
But the only thing i can't do is using spotlight like i want: search only returns file that contain the word i searched in filename, spotlight would be able to search also in the text of the documents.
I was able to do this on a NAS that could share folders by using AFP.
I think that it was a linux-based NAS, so this would be possible (i think).
Anyone have some suggestions?

Thanks a lot everyone (and sorry for my english if so).

---

