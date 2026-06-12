---
title: "Not able Update"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Bharath on 2006-12-16
Hi,

When I click on update icon I am getting the following error mesg:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

what should I do.....pls help me put
Bharath

---

### Post by xyz on 2006-12-16
Hi,
Have you added the necessary repositories? Check howto here:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by argie on 2006-12-16
> **Bharath said:**
> Hi,

When I click on update icon I am getting the following error mesg:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

what should I do.....pls help me put
Bharath

First copy out the file (in case we need it later)
```
cp /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages ~/ 
```

Then delete it
```
sudo rm -vf /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages 
```

If that displays an error with some other Package list, then delete the whole lot with
```
sudo rm -vf /var/lib/apt/lists/*
```

I'm not sure if that last part can finish you off, so make sure to backup.

---

### Post by Bharath on 2006-12-26
Hi,

thanks for your help, I was able to solve the issue as suggested by you guys.

I apologize for the delay in replying as I was away on vaction for sometime.

Bharath

---

### Post by Sef on 2006-12-26
> Hi,

thanks for your help, I was able to solve the issue as suggested by you guys.

I apologize for the delay in replying as I was away on vaction for sometime.

Bharath

No problem.  Thanks for letting us know that you resolved your problem.

---

### Post by thomas576 on 2007-03-23
thanks for this information it was very usefull, if only it was in the man page i was so stuck!

---

