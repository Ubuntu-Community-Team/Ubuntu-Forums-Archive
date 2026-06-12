---
title: "&quot;Add/Remove Applications&quot; problem"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-18
Yesterday it was working fine.  But today everytime I try to install an Application (even Ubuntu supported) I get the following:

dpkg: syntax error: unknown user 'amavis' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

Thanks for any help.

---

### Post by louis_nichols on 2007-03-18
Try running this command:

```
sudo apt-get -f install 
```
This should get rid of the error. As for the package that caused this, you should file a bug report in launchpad.

---

