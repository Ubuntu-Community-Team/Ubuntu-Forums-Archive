---
title: "dont know what to install"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by izibizi on 2007-06-24
hi all,

i need a very simple esrver box.

i only need simple ftp and telnet access to it to be used internally only.

i need full access like root.

no firerwall, no security. nothing.

i like gui to manage it.

please advice what version/type should i install.

---

### Post by louieb on 2007-06-24
telnet and GUI are two different things. The easiest thing to do is install ssh-server on the Linux box. Then use ssh in a terminal window from a Linux client. OR install Putty on your windows client and use it.

---

### Post by Phixion on 2007-06-24
Install the Server version of Ubuntu, install proftpd then you can ftp to the server with your linux username and pass.

SSH server should be automatically installed with server version.

---

### Post by louieb on 2007-06-24
> **Phixion said:**
> SSH server should be automatically installed with server version.
Only the ssh client is automatically  installed.

---

### Post by Phixion on 2007-06-24
> **louieb said:**
> Only the ssh client is automatically  installed.

Nothing apt-get can't handle.

---

### Post by izibizi on 2007-06-24
the server verion comes up in text mode and for me its like - what the hell i do now??

how do i install proftpd in text mode and how do i configure it to let me connect from windows?

---

### Post by h0ax on 2007-06-24
login to the box with your username / pw
type the command:
```
sudo apt-get install proftpd
```
that will install the ftp daemon.
it will be automatically configured to the username/pw you set up on the install.

If you want a separate account you'll have to set that up manually - try searching the forums - there are lots of great HOWTO's on that process.

---

