---
title: "user not added as sudoer, and no root account to speak of"
date: 2009-05-06
forum: Apple Hardware Users
---

### Post by druca on 2009-05-06
Hi, I just installed 9.04 on my ppc mac, the only option was text install, etc etc, now fast forward to the full install and I cannot use sudo, and there is no root account that I can see or at least gain access to.   

Is there something goofy like single user mode ( mac thing ) I can do for Ubuntu and add myself to the admin group? Is it booting up with the cd and then doing something similar to single user mode?

I would like to get rid of selinux, does the new fast booting software depend on selinux?

---

### Post by undertakingyou on 2009-05-06
There is a single user mode. In your grub menu during boot there is a recover option, that is single user mode. You can then fix your sudo problem.

---

### Post by druca on 2009-05-06
awesome thank you!!

---

### Post by mkvnmtr on 2009-05-07
First a ppc install does not use grub it uses yaboot. To use sudo open a terminal and start your command with sudo. It will ask for a password .Use the password that you used installing the system. You might also wish to read the Ubuntu instructions. All this information is explained in a much better manner than I can.

---

### Post by cyberdork33 on 2009-05-07
for the record, I think that on ppc, you get to recovery mode by doing 'linux single' at the yaboot prompt.

---

