---
title: "Help setting up a Ubuntu file server"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by spenser on 2007-07-17
I am trying to set up a Ubuntu fileserver to work in a Windows based environment.  I currently have 3 hard disks on this server:

40 GB for the OS
250 GB for Files
250 GB as a backup for the previous HDD

What i want to do is set it up so that the network can access one of the 250GB HDDs and use it as a fileserver through the Windows network, and at night have the two disks sync so that everything will be backed up.  

Please advise me as how to go about mounting my drive and sharing it through the network so that the Windows workstations may access the files.

Thank you all very much and I look forward to your replies.

-Spenser

---

### Post by finer recliner on 2007-07-17
you probably want samba.

check out this tutorial for configuring it:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba))

---

