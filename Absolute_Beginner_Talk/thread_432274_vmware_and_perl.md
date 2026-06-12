---
title: "vmware and perl"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Firex726 on 2007-05-03
Hello,

I just want to say I am an absolute beginner at Ubuntu...

Anyways to the point; I am trying to install VMware Server, and I have no issues extracting the tar and navigating to the right directory via the terminal, and when I get there to try and run the perl script (vmware-install.pl) I get an error (bash: vmware-install.pl: command not found) After reviewing the script it says that I need to have my perl installed to:

/usr/bin/perl

And when I look there it is installed there, but I am not sure what else to do. Someone suggested I run perl then run the script from within it, but have no idea how to do this either. 

Any advice?

---

### Post by rhysmc on 2007-05-03
Hi,

This can be a little difficult to install. To clarify the following does not work:

```
cd {vmware-dir}
sudo su
./vmware-install.pl
```

Ensure you put   ./

---

