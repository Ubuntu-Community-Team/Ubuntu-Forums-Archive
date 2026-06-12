---
title: "[SOLVED] I'm looking for a way to transfer files over ssh..."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-09-13
I'm trying to figure out how to transfer files over ssh.  I have a server that I need to transfer files to.  Is there anyway to do this via ssh?  I have openssh-server on the server machine.

---

### Post by sumguy231 on 2007-09-13
You can, using scp. It's done like this:

```
scp <file you need to transfer> user@server:/place/to/put/file
```
For more info, type 'man scp'.

If you're using KDE, you can just type 'fish://user@host' to copy files over graphically, which is really nice.

---

### Post by zetsumei on 2007-09-13
is that already installed by default in fluxbuntu or will I need to install it?

---

### Post by scxtt on 2007-09-13
scp is provided by ssh.
```
:> aptitude show openssh-client
Package: openssh-client
State: installed
Automatically installed: no
Version: 1:4.3p2-8ubuntu1
Priority: standard
Section: net
Maintainer: Colin Watson <cjwatson@ubuntu.com>
Uncompressed Size: 1659k
Depends: libc6 (>= 2.5-0ubuntu1), libcomerr2 (>= 1.33-3), libedit2 (>= 2.5.cvs.20010821-1), libkrb53 (>=
         1.4.2), libncurses5 (>= 5.4-5), libssl0.9.8 (>= 0.9.8c-1), zlib1g (>= 1:1.2.1), debconf (>= 1.2.0) |
         debconf-2.0, adduser (>= 3.10), dpkg (>= 1.7.0), passwd
Suggests: ssh-askpass, xbase-clients
Conflicts: ssh (< 1:3.8.1p1-9), sftp, rsh-client (< 0.16.1-1), ssh-krb5 (< 1:4.3p2-7)
Replaces: ssh, ssh-krb5
Provides: rsh-client, ssh-client
Description: Secure shell client, an rlogin/rsh/rcp replacement
 This is the portable version of OpenSSH, a free implementation of the Secure Shell protocol as specified by
 the IETF secsh working group.

 Ssh (Secure Shell) is a program for logging into a remote machine and for executing commands on a remote
 machine. It provides secure encrypted communications between two untrusted hosts over an insecure network.
 X11 connections and arbitrary TCP/IP ports can also be forwarded over the secure channel. It is intended as a
 replacement for rlogin, rsh and rcp, and can be used to provide applications with a secure communication
 channel.

[color=red] This package provides the ssh, scp and sftp clients, the ssh-agent and ssh-add programs to make public key
 authentication more convenient, and the ssh-keygen, ssh-keyscan, ssh-copy-id and ssh-argv0 utilities.[/color]

 --------------------------------------------------------------------

 In some countries it may be illegal to use any encryption at all without a special permit.
```

---

### Post by zetsumei on 2007-09-13
thanks for the help SOLVED.

---

