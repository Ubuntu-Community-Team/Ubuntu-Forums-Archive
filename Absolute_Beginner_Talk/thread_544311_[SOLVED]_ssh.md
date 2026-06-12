---
title: "[SOLVED] ssh"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Yizi on 2007-09-06
Hello,

I hear Linux comes with build in SSH, how can i access SSH?

---

### Post by be4truth on 2007-09-06
It's not build in. But you can install it:

Secure shell client and server 

```
sudo apt-get install ssh
```

---

### Post by llamakc on 2007-09-06
Open a terminal and type "ssh [EMAIL="USER@I.P.ADD.RESS"]USER@I.P.ADD.RESS[/EMAIL]" where user is the remote user and I.P.ADD.RESS is the IP OR NAME of remote machine.

If you want to run the server you must install "openssh-server".

The package mentioned in the post above is a transitional package that provides BOTH the client and the server. Since your first post did not specify which one you need, that would be a correct answer too.

```

ken@llamakc 06:14:20:~$ apt-cache show ssh
Package: ssh
Priority: optional
Section: net
Installed-Size: 32
Maintainer: Colin Watson <cjwatson@ubuntu.com>
Original-Maintainer: Matthew Vernon <matthew@debian.org>
Architecture: all
Source: openssh
Version: 1:4.3p2-8ubuntu1
Depends: openssh-client, openssh-server
Filename: pool/main/o/openssh/ssh_4.3p2-8ubuntu1_all.deb
Size: 1086
MD5sum: 71edf0d0fd6fb06b4ce16b05d9af5361
SHA1: 6019bc28b4e6880d0b461b0e0d8f88c0759f5731
SHA256: a814438758f3ef0b59ab34a65aedd0dd2e56e839d72bf8b096fee58722afd933
Description: Secure shell client and server (transitional package)
 This is a transitional package depending on both the OpenSSH client and
 the OpenSSH server, which are now in separate packages. [B]You may remove
 it once the upgrade is complete and nothing depends on it.[/B]

```

However, the client IS provided by default and is in the "main" repository for a normal Ubuntu/Kubuntu install.

---

### Post by coxy on 2007-09-06
It depends what you need, there are both the client and server packages.

```

sudo apt-get install openssh-client openssh-server

```

This will setup the server to run on port 22 and start the service. You can change the server settings via /etc/ssh/sshd_config

To use the client on the command line is quite simple.

```

ssh username@hostname

```

For more infor look at the man page.

```

man ssh

```

---

### Post by Yizi on 2007-09-06
Thanks everyone, problem is solved, the infomation was enough :D

---

