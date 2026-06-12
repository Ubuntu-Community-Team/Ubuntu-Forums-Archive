---
title: "Synaptic Server issues"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by jackmc on 2007-07-26
I just tried to install a few things, and each time a get a message like the following. It happens for apt-get, synaptic, and add/remove...

```

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/g/gawk/gawk_3.1.5.dfsg-4build1_i386.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-18_all.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/multiverse/libf/libfame/libfame-0.9_0.9.1-0.2_i386.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/f/flac/libflac++5c2_1.1.2-5ubuntu2_i386.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/p/pvm/libpvm3_3.4.5-7_i386.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)


W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.0.2-0.8ubuntu3_i386.deb
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)



```

Please help me

---

### Post by panther_sn on 2007-07-26
I was having a similar problem and I think its something to do with the au.ubuntu  Sooo I went to System > Administration > Synaptic Package Manager
then opened the settings menu chose repositories and in the Ubuntu Software tab changed 
"Download from" from Server for Australia, to Main Server, and all has worked fine since. Hope that helps

---

### Post by jackmc on 2007-07-26
thanks, that fixed it :)

---

### Post by Seisen on 2007-07-26
Those repositories are down as of right now and they have been for about two days.

---

### Post by pyros on 2007-07-26
Yeah, unfortunatly it happens from time to time.  you usually get better performance from your local mirrors though, so I would personally recommend switching back when they come back up. (less strain on the main repos too)

---

