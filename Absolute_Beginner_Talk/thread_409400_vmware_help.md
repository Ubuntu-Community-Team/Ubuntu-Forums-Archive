---
title: "vmware help"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by prplhaz999 on 2007-04-14
I am trying to install vmware tools on dapper. I get the error:

None of the pre-built vmhgfs modules for vmware tools is suitable for your running kernel. Do you want this program to try to build the vmhgfs module for your system? (you need to have a C compiler installed on your system) [yes]

What is the location of the "make program on your machine?


Now I don't know what a C compiler is or does or even how to install one and I can't get past this point. Can someone be gracious enough to explain what I have to do?

---

### Post by Bachstelze on 2007-04-14
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by Maestro23 on 2007-04-14
Vmware Tools Doc: [https://help.ubuntu.com/community/VMware/Tools?action=show&redirect=VmwareTools](https://help.ubuntu.com/community/VMware/Tools?action=show&redirect=VmwareTools)

---

### Post by prplhaz999 on 2007-04-14
That worked perfectly thanks. Just one question though. What exactly did I just do?
:confused:

---

### Post by Bachstelze on 2007-04-14
If you did what I told you, you installed gcc, all the standard libraries required to compile C code and the kernel headers maching your current running kernel (they're needed to compile kernel modules, like the vmware ones).

---

### Post by scxtt on 2007-04-14
installed the tools that will allow your computer to "build" necessary modules for vmware ... it's also not specific to vmware - you just needed the tools in this case for vmware modules ... the same thing is necessary for building graphic card drivers, etc. ...

---

### Post by prplhaz999 on 2007-04-14
Fantastic! I appreciate everyone's help.
:guitar:

---

