---
title: "Error...!"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-16
I issued this command:

```
sudo apt-get update
```

and I recieved the following messege after 10 mins:

> gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
  Sub-process gzip returned an error code (1)
Fetched 3463kB in 7m37s (7573B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

What does it mean?

---

### Post by jasmuz on 2005-08-16
It means that the package list in that server is corrupted.

---

### Post by Nequeo on 2005-08-16
I assume this is a major problem affecting anyone using the US server, and will probably be recitified by the time you read this. 

If not, open up /etc/apt/sources.list with whatever editor you like, and change every instance of 'us.' to 'au.'!

The Australian mirrors are still working fine :)

---

### Post by Muhammad on 2005-08-17
OK, the us server is working again, but I have a new problem now...

I issued the same command and recieved the following error:

> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

 :-?

---

### Post by Nequeo on 2005-08-17
You may have fixed this by now... because you usually get that message when you try to run an apt-get command while Synaptic or the Ubuntu Update Manager are running.

---

