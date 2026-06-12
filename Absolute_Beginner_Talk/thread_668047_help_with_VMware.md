---
title: "help with VMware"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-01-15
i didnt like to much virtualbox.. so ill try VMware.... can someone help me with the installation i have searched but havent found a guide

---

### Post by Toet on 2008-01-15
I use the free version vmware player. You can download it here:

[http://www.vmware.com/download/player/]("http://www.vmware.com/download/player/")

Download the .tar.gz and unzip it in a directory.

Go into the directory and use the installer:

```
sudo ./vmware-install.pl
```

I always answer the questions by hitting enter to get the default settings.

Done.

I use Qemu to create virtual machines: [http://cri.ch/linux/docs/sk0020.html]("http://cri.ch/linux/docs/sk0020.html")

---

### Post by hyper_ch on 2008-01-15
vmware server is in the repos. Might be in the canonical ones so you might have to add them also (not sure in which repos it is).

after that:

```

sudo apt-get install vmware-server

```

Then to go vmware's site and get yourself a registration code:

it's free of charge:  [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

---

