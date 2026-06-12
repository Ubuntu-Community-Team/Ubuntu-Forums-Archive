---
title: "Running Chkrootkit"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Knewguy on 2007-01-24
I installed chkrootkit from Synaptic and need help running it.

I opened a terminal and typed in chkrootkit and I got an error message telling me I need root privileges.

I don't want to mess up my system by doing something wrong in root.

Also, is there a GUI for this program (that makes it easier for me to use)?

Thanks for the help.

---

### Post by crossedout on 2007-01-24
No worries on harming the system.

Type:
```
sudo chkrootkit
```

Enter your password and let it ride.

-Xout

---

### Post by Knewguy on 2007-01-24
That worked....and everything clean. :) 

Thanks.

---

### Post by ardchoille42 on 2007-01-24
> **Knewguy said:**
> That worked....and everything clean. :) 

Thanks.

You might also want to install and run rootkit hunter as it checks for different things than chkrootkit checks for. Rootkit Hunter can be found [here]("http://www.rootkit.nl/").

I run both chkrootkit and rkhunter on a daily basis.

---

### Post by Knewguy on 2007-01-24
I ran rkhunter and I think a false positive came up?

(I remove my username in the example)

gpg: WARNING: unsafe ownership on configuration file `/home/NAME/.gnupg/gpg.conf'

Thanks for the help.

---

### Post by ardchoille42 on 2007-01-24
> **Knewguy said:**
> I ran rkhunter and I think a false positive came up?

(I remove my username in the example)

gpg: WARNING: unsafe ownership on configuration file `/home/NAME/.gnupg/gpg.conf'

Thanks for the help.

Well, yes, that's true.

---

