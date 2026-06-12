---
title: "More Vmware Problems"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2007-06-14
Trying to install following this link [http://howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto]("http://howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto") but I get as far as the installing part and get this

scotty@Buntu:~/vmware-server-distrib$ sudo vmware-install.pl
sudo: vmware-install.pl: command not found

I looked for myself and the file is there but has a lock on it. How do I unlock it?

---

### Post by apjone on 2007-06-14
from within the directory run

```

sudo ./vmware-install.pl

```

If that does not work do 

```

sudo chmod +x vmware-install.pl
sudo ./vmware-install.pl

```

---

### Post by eentonig on 2007-06-14
A smarter way, would be to install it from the repositories.

enable the commercial repo and 

> sudo apt-get install vmware-server vmware-server-lernel-modules

You will have a problem afterwards to run your VM's, but this is easily solved by downloading and running the "vmware-any-any-update" patch.

I posted a vmware installation problem today and posted the solution in there as well.

---

### Post by Mac70 on 2007-06-14
Im now getting a previous installation error. Whats the "-r" command?

---

