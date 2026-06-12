---
title: "Sudo and Su help"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-08-17
Whenever I try typing a command "sudo ______", it always gives me an error "sudo: must be setuid root".  Apparently, I shouldn't have chown'd my usr directory.  Is there any way to fix this without reinstalling.

Also, when I enter "su", and then my password, it says that my password was incorrect, even though I am 100% sure that it was correct.  Does this also have to do with chown'ing my usr directory?  Is there any way to fix it?

Thanks.

---

### Post by Bachstelze on 2007-08-17
> **Yes said:**
> Whenever I try typing a command "sudo ______", it always gives me an error "sudo: must be setuid root".  Apparently, I shouldn't have chown'd my usr directory.  Is there any way to fix this without reinstalling.


No. And su doesn't work because it needs root's password, not yours.

---

### Post by Cypher on 2007-08-17
Boot into the Recovery Mode from the GRUB menu, then at the command prompt do the following
```

cd /usr/bin
chmod o+s sudo

```
Also revert the USR directory to back what it was before and give it a shot..

---

### Post by Yes on 2007-08-17
You mean it needs the root password that I set up when I installed?  Because I'm using that password, and it still doesn't work.

---

### Post by Bachstelze on 2007-08-17
You didn't set up a root password when you installed.

---

### Post by diatribe on 2007-08-17
ubuntu does not allow su by default, sudo will allow you to use your user pass

---

### Post by Deived on 2007-08-17
you have to enable root.  I'm not at my computer now, but I think the command is something like..
```
sudo passwd root
```
You then give root a password.  After that, sudo and su - should work fine.

---

### Post by Yes on 2007-08-17
I rebooted using the Ubuntu Live CD, and ran the commands 

```
chmod o+s sudo /media/disk/usr/bin/
chown root:root /media/disk/usr/bin/sudo
chmod 4755 /media/disk/usr/bin/sudo
```

Then I rebooted from the hard drive, and sudo works!  I also ran Deived's command, now su works too!  Thank you!

---

### Post by Bachstelze on 2007-08-17
Problem solved for now but if you chown'ed /usr, expect more problems later.

---

### Post by Yes on 2007-08-17
Like what?

---

