---
title: "Boot with OS X and Ubuntu?"
date: 2006-09-18
forum: Apple PPC Users
---

### Post by ferose2 on 2006-09-18
Can anyone tell me how I can dualboot with OS X and Ubuntu. I have both OS installed but only Ubuntu boots up, OS X just takes up harddrive space.

---

### Post by sbentzen on 2006-09-18
well it'd be a lot more helpful if you were to tell us if you are using the ppc chip or the x86 chip, if you are using ppc you have to edit the yaboot.conf (don't ask me how i am new too) or if you are using the x86 chip you have to edit something with grub.

---

### Post by linear on 2006-09-18
Assuming yaboot is set up more or less correctly, and you want OS X to be the default, you need to edit /etc/yaboot.conf and add the line:

**defaultos=macosx**

After this, you need to install the new config:

**sudo ybin -v**

---

### Post by ferose2 on 2006-09-19
I am using the x86 version.

---

