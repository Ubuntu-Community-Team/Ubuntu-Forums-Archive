---
title: "Synaptic error meassage"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-06-25
When I open Synaptic I get this error message

Quote:

The following problems were found on your system:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How do I fix this please?

---

### Post by BobCFC on 2007-06-25
Go to Applications->Accessories->Terminal and paste

```
sudo dpkg --configure -a
```


After that try again it might  say another error about sudo apt-get install -f

If so paste in terminal again
```

sudo apt-get install -f
```

---

### Post by a.v.l on 2007-06-25
> **BobCFC said:**
> Go to Applications->Accessories->Terminal and paste

```
sudo dpkg --configure -a
```


After that try again it might  say another error about sudo apt-get install -f

If so paste in terminal again
```

sudo apt-get install -f
```

Thank you, using the first command seems to have fixed the problem, much obliged.

---

