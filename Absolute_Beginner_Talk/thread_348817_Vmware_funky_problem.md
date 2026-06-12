---
title: "Vmware funky problem"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-01-29
I have this error that I keep getting while trying to install via terminal:

```
./vmware-install.pl: 8: use: not found
./vmware-install.pl: 14: use: not found
./vmware-install.pl: 17: my: not found
./vmware-install.pl: 18: my: not found
./vmware-install.pl: 19: my: not found
./vmware-install.pl: 20: my: not found
./vmware-install.pl: 21: my: not found
./vmware-install.pl: 22: my: not found
./vmware-install.pl: 23: my: not found
./vmware-install.pl: 24: my: not found
./vmware-install.pl: 25: my: not found
./vmware-install.pl: 26: my: not found
./vmware-install.pl: 27: my: not found
./vmware-install.pl: 28: my: not found
./vmware-install.pl: 31: my: not found
./vmware-install.pl: 34: my: not found
./vmware-install.pl: 38: my: not found
./vmware-install.pl: 39: my: not found
./vmware-install.pl: 40: my: not found
./vmware-install.pl: 41: my: not found
./vmware-install.pl: 42: my: not found
./vmware-install.pl: 43: my: not found
./vmware-install.pl: 44: my: not found
./vmware-install.pl: 46: my: not found
./vmware-install.pl: 47: my: not found
./vmware-install.pl: 48: my: not found
./vmware-install.pl: 49: my: not found
./vmware-install.pl: 50: my: not found
./vmware-install.pl: 53: sub: not found
./vmware-install.pl: 54: undef: not found
./vmware-install.pl: 55: undef: not found
./vmware-install.pl: 56: undef: not found
./vmware-install.pl: 57: undef: not found
./vmware-install.pl: 58: undef: not found
./vmware-install.pl: 60: Syntax error: word unexpected (expecting ")")

```

I have downloaded the workstation twice and it still gives me that error. It use to work before but now it doesn't. Please do help. :guitar:

---

### Post by Bagboy23 on 2007-01-29
Anyone know what all this is about?

---

### Post by blurryone on 2007-12-11
dang, i have this very same error!!! anybody figure this out?

xxxxx@xxxxxxxxxxx:~/Desktop/VMware-workstation-linux/vmware-distrib$ sh vmware-install.pl
vmware-install.pl: 8: use: not found
vmware-install.pl: 13: use: not found
vmware-install.pl: 16: my: not found
vmware-install.pl: 18: my: not found
vmware-install.pl: 20: Syntax error: "(" unexpected

thanks all
Blurry

---

### Post by Threbus5 on 2007-12-12
Did you download it twice from the same place?

Try another mirror?

Does VMware require a clean install? 

I recall that once I aborted an install and attempted another install without removing the partial. Instead of attempting an over-write, the second install aborted.

Best of luck.

---

### Post by blurryone on 2007-12-12
nope i was just using the wrong command.....

followed [this]("https://help.ubuntu.com/community/VMware/Workstation") guide and it worked fine

woop woop

cheers
Blurry

---

