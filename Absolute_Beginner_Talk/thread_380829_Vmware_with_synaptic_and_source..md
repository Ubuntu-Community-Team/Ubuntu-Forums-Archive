---
title: "Vmware with synaptic and source."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-03-10
Hi, i am trying to install VMware. Originally i installed the vmware player and then server packages from the repositories. Then when i realised that they weren't the right files to run windows in, so i downloaded VMware from the site. When i run:
```

sudo ./vmware-install.pl
```

I get this:

[I]A previous installation of VMware software has been detected.

Failure

Execution aborted.[/I]

I have done a "complete removal" of the previous packages from synaptic and i still get this. Is there some way i can find and remove any files that could have been left over? or some bypass command that forces this install to ignore the "previous installation found" error?


also i get this:
[I]VMware Workstation is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.[/I]

The Workstation has not been installed yet as this is what i am trying to install. And there are no vmware files in /usr/bin like it thinks there are.

---

### Post by joselin on 2007-03-10
Try to delete /etc/vmware folder.

---

### Post by ajmorris on 2007-03-10
> **joselin said:**
> Try to delete /etc/vmware folder.

Thank you so much!! That folder was empty but it worked when i deleted it. :)

---

