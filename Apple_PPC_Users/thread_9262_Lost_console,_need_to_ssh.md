---
title: "Lost console, need to ssh"
date: 2004-12-26
forum: Apple PPC Users
---

### Post by xico on 2004-12-26
Hello,
Ubuntu first boot: I have to reconfigure Xserver but I lost console access: I'm stuck in misconfigured Xserver with a black screen.
Ctrl+Alt+F2
Ctrl+Alt+Enter
don't work.
I can't reach with a live cd either (oldworld mac)
I tried to ssh from the Terminal of another mac on the LAN (this worked the other way since I copied the kernel and initrd from ubuntu to the distant mac):
sudo ssh 10.0.0.1
ssh: connect to host 10.0.0.1 port 22: Connection refused

Any thoughts would be appreciated. Thanks.

Francois

---

### Post by xico on 2004-12-27
...something I don't really understand  is the fact that I was able to scp the two files without installing ssh as described in the wiki  [http://www.ubuntulinux.org/wiki/SSHHowto](http://www.ubuntulinux.org/wiki/SSHHowto)
So is SSH installed by default or not? And why can't I reach the distant mac now?

Thanks for answering

Francois

---

### Post by rbran100 on 2004-12-27
I am pretty sure, although i havn't used the MAC version.  That at the bootloader there was a "safe" boot option.  You should be able to boot into that which will automatically give you console at boot.  

-Rich

---

### Post by xico on 2004-12-28
I've been able to recover a kind of console (very bad video display) entering "single" in the kernel arguments of bootX.

---

### Post by az on 2004-12-28
"So is SSH installed by default or not"

I think the ssh-client is installed but the server is not, for security reasons ( no opened ports...)

---

### Post by guu on 2005-06-03
In practice, running sshd in version 2 only mode, with root login disabled, and assuming your password is *good* is, IMHO, secure practice.

A brute force attack on ssh, while easy to set up, is not only likely to fail to get you in, but will generate tons of log entries.

Furthermore, if ssh is built with tcp-wrappers, it can be installed with hosts.deny set to ALL: ALL and an optional IP address in hosts.allow based on a setup query...

Of course, no services is the safest config of all, but it's pretty damn useless as well. I can see why a distro targetting the novice user would not run ssh by default, but it could offer it as a setup option, in the same way that a Ubuntu install supports changing the filesystem type (which made me very happy, since I could go with reiser and avoid the ridiculous ext2 fsck that ext3 likes to run).

I am babbling off-topic.

---

