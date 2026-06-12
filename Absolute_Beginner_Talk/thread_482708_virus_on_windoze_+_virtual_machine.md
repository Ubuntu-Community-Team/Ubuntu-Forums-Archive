---
title: "virus on windoze + virtual machine?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-24
Ok, i'm curious, let's say i installed a virtual machine on windows running ubuntu or <insert preferred linux distro here>. Then my windows gets a virus and eats everything. Would my linux virtual machine still be unaffected by it? MY previous post talks about vice-versa, so now it's the other way round.

---

### Post by tgoose on 2007-06-24
Since the "virtual" operating system is made of files within the host one, a virus on the host system will not treat the virtual machine's files any differently. If all files are destroyed, then the virtual ones will too.

---

### Post by freebird54 on 2007-06-24
Of course, once this disaster has happened, you restore the snapshot of the operating VM as it was before the virus hit, and continue on undisturbed....

It can only hurt the virtual machine it's running on - so a snapshot is complete protection!  :)

---

### Post by kvonb on 2007-06-24
The only way a Windows virus will effect your VM is if it deletes the whole VM file, it can't do anything to the individual Linux files because Linux doesn't run Win code.

Unless of course you have WINE running inside your VM and you execute infected Windows code, then it might possibly be able to damage the Windows files (theoretically), and (as a worse case scenario) maybe even some stuff inside your home folder, but not the VM Linux itself, ie it will still boot.

But that would be extremely unlikely as WINE would spit the dummy first I'm sure :).

---

