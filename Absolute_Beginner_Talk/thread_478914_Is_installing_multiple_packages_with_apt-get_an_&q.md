---
title: "Is installing multiple packages with apt-get an &quot;atomic&quot; transaction?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by uber_n00ber on 2007-06-19
While [reading about setting up the server edition of Ubuntu]("http://doc.ubuntu.com/ubuntu/serverguide/C/apt-get.html"), I found this in regard to using the apt-get command:

> Multiple Packages: You may specify multiple packages to be installed or removed, separated by spaces.

Which got me wondering: would that be considered an "atomic" transaction? (I'm thinking like a database transaction here...) For instance, using the following command:

```
sudo apt-get install package1 package2 package3
```

... if package1 installed OK and package2 installed OK, but package3 failed to install, would there be a "rollback"? i.e.package1 and package2 would be uninstalled?

---

### Post by KIAaze on 2007-06-19
No.

If that's the case, it will probably suggest to run "dpkg --configure -a" the next time you try to install something (or directly after the failure).
This command tries to finish the installation again.

It happened to me quite often during system upgrades. And I never noticed that apt reinstalled already installed packages after a "failure". It only tries to repair broken packages.

In some cases, you don't want the installation to continue. In that case, see here:
[http://www.linuxquestions.org/questions/showthread.php?t=557950]("http://www.linuxquestions.org/questions/showthread.php?t=557950")

---

### Post by uber_n00ber on 2007-06-19
Thanks KIAaze! Good to know...

---

