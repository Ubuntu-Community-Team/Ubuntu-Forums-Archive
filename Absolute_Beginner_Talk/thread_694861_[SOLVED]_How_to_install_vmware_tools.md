---
title: "[SOLVED] How to install vmware tools?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-02-12
ok i have vmware workstation and I'm virtualizing ubuntu 7.10 but when i go to install vmware tools it mounts the virtual drive and everything but there is no deb file only rpm and the source.. so how do i compile from source?

thanks in advance for the newb question...

---

### Post by PCFascist on 2008-02-13
I've heard that you'll have better luck with a premade image for VM:

[http://www.thoughtpolice.co.uk/vmware/](http://www.thoughtpolice.co.uk/vmware/)
or 
[http://jars.de/linux/ubuntu-710-vmware-image-download-english](http://jars.de/linux/ubuntu-710-vmware-image-download-english)
or
[http://www.vmware.com/appliances/directory/1066](http://www.vmware.com/appliances/directory/1066)

But if your too far into it....

[http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/](http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/)

---

### Post by mordox on 2008-02-13
convert rpm to deb using alien otherwise install rpm install using the rpm command rpm -ivh *.rpm:guitar:

---

### Post by dcstar on 2008-02-13
> **kamitsukai said:**
> ok i have vmware workstation and I'm virtualizing ubuntu 7.10 but when i go to install vmware tools it mounts the virtual drive and everything but there is no deb file only rpm and the source.. so how do i compile from source?

thanks in advance for the newb question...

It is not really "source", just run it and see what happens. If things are missing, install the **build-essential** meta-package.

There is a whole Virtualization sub-forum with answers on this topic.

---

