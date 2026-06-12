---
title: "Vmware Server"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by DapperDanMan on 2007-08-24
I'm new to (K)Ubuntu. How can I install VMServer on my machine? Is it possible to install RPM? All thoughts are appreciated. Thanks in advance

---

### Post by tszanon on 2007-08-24
> **DapperDanMan said:**
> I'm new to (K)Ubuntu. How can I install VMServer on my machine? Is it possible to install RPM? All thoughts are appreciated. Thanks in advance
Download VMware Server from [www.vmware.com](www.vmware.com) (not the RPM, the .tar.gz version);
Register to get your free serial number;
Extract the .tar.gz archive (just double-click the file, it will open in file-roller);
Go to the terminal;
cd to the vmware directory;
I don't quite remember now, but, if I recall correctly, the right script is ```
./vmware-install.pl
```
Follow the instructions. :)

I'll have to do it again soon, so I probably will be able to help you if you have any problems.

---

### Post by fjgaude on 2007-08-25
Say, the vmware server is in Synaptic.

And do the ./install as root, i.e., with sudo.

frank

---

### Post by tszanon on 2007-08-25
> **fjgaude said:**
> Say, the vmware server is in Synaptic.

And do the ./install as root, i.e., with sudo.

frank
Well, not in Dapper, where there is only vmware player. If vmware server can be found in edgy's/feisty's repositories, I don't know.

---

### Post by fjgaude on 2007-08-25
It's in Feisty and that's what I'm using... very quick and pain free install.

frank

---

### Post by DapperDanMan on 2007-08-26
I found these instructions and have installed vmware server. Very easy

---

### Post by DapperDanMan on 2007-08-26
sorry here is the link

[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by msutton86 on 2007-08-31
I don't know if you already figured it out, and if you did sorry for bringing this back up, but VMware Server is in the synaptic installer.  It's also in add remove programs.  i haven't tried it out yet, but am going to do so in about 15 mins;  Once Acronis is done doing it's thing. So if you any advice please feel free to throw it all out.

---

### Post by schmitty2005 on 2007-08-31
Here is another how to:

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

:guitar:

---

### Post by DapperDanMan on 2007-11-10
Anyone having problems upgrading the new VM Server? I get errors on upgrade and remains in list of auto updates. Any thoughts would be appreciated

---

### Post by scorp123 on 2007-11-10
[http://ubuntuforums.org/showthread.php?t=605857](http://ubuntuforums.org/showthread.php?t=605857)
[http://ubuntuforums.org/showthread.php?t=605439](http://ubuntuforums.org/showthread.php?t=605439)
[https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683](https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683)

---

### Post by DapperDanMan on 2007-11-11
Thanks for the reply. Hopefully this will be addressed in the future

---

### Post by Butthead on 2007-11-11
Hmm, has anybody else (who also suffers from this problem) had Adept make a successful new package retrieval since this problem has surfaced? :confused:

Adept seems to always time out at about 66% for me during installation of the new packages (claims the new packages it retrieved have installed successfully though). :(

---

