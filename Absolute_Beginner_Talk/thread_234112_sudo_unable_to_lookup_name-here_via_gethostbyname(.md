---
title: "sudo: unable to lookup *name-here* via gethostbyname()"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by astralon on 2006-08-11
hello

i wanted to change my machine's name so i edited /etc/hostname.

restart and the name is changed but sudo and all system->administrator commands do not work. 

i guess it's probably because there's a different name in /etc/hostname and /etc/hosts.

but i can not make sudo in order to edit these two files.

any help?

---

### Post by astralon on 2006-08-11
i entered 'recovery mode'. problem solved.

---

### Post by jpkotta on 2006-08-11
Grrr...this is an old bug.  Why won't they fix it?  I even submitted a crappy proof-of-concept script to fix it.

Anyway, you can log in as root by rebooting in "recovery mode".  Fix it there and then reboot again.

---

### Post by kenlyle on 2007-05-09
What exactly does this error message mean?

And what exactly is the "fix".  I see that it may involve recovery mode, and something to do with /etc/hosts and/or etc/hostname....

OK...investigating, it appeared that my hostname file said edubuntu2, and my hosts file had a line with an IP address and edubuntu, which I changed to edubuntu2, and that seems to have made this error go away.

Best of Luck,
Ken

---

