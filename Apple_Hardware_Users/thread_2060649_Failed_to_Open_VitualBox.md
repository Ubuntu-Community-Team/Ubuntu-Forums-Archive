---
title: "Failed to Open VitualBox"
date: 2012-09-20
forum: Apple Hardware Users
---

### Post by trevorshinder on 2012-09-20
hello, 

i was hoping someone could help me with an error message i am receiving when trying to open my virtual box.  i am running it on my new macbook pro running version 10.8.2, processor: 2.3 GHz intel core i7 and this is the error messages i am receiving:

[INDENT]Failed to open a session for the virtual machine ilsonsystem.

VT-x is being used by another hypervisor. (VERR_VMX_IN_VMX_ROOT_MODE).

VirtualBox can't operate in VMX root mode. Please close all other virtualization programs. (VERR_VMX_IN_VMX_ROOT_MODE).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
[/INDENT]

i googled my error and i found a similar thread saying someone typed the following code:

```
sudo /etc/init.d/vboxdrv setup
```

and it fixed their issue but i am not sure where i am typing this code.  i am running linux ubuntu on my virtualbox system.

if anyone could help i would greatly appreciate it!

---

### Post by howefield on 2012-09-20
You would enter the command in a terminal window although I'd doubt it will fix your issue.

---

