---
title: "Copy files from local to remote using Nautilus - No Resume?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-04-14
I've setup a remote server and I can connect to it on my local machine using: "Places->Connect to Server..." using SSH connection.
But because the server is remote I am at the mercy of my cable internet connections bandwidth (2mb/s upload), so when I try and upload a 10gig file it takes many hours to do.  Which is the nature of the beast I understand, but the problem I am having is that Nautilus won't allow me to resume the transfers when I copy a file using Nautilus into the remote server's directory (again using Nautilus).  But if I am using a windows machine and WinSCP I can resume transfers...

So how come I can't resume transfers using Nautilus? is there a way to do this?
Or is there a WinSCP equivalent for Ubuntu?
Thanks,
-BassKozz

p.s. I also tried installing Konqueror, and I couldn't figure out how to Resume using it either... am I missing something or do both Nautilus and Konqueror not support resume via SSH/SFTP?

---

### Post by BassKozz on 2008-04-14
After further research I've found an app that will allow for Resume [gFTP]("http://gftp.seul.org/") :D

Now does anyone know if it's possible to resume using Nautilus or Konqueror via SSH/SFTP?

---

