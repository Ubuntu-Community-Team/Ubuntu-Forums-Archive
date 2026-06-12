---
title: "winSCP3 equivalent for ubuntu"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-23
Hi,

I have been using WinSCP3 to transfer files via ssh - what SIMILAR program to you recommend to use on Ubuntu.

thx,
ben

---

### Post by Cypher on 2008-01-23
Install the openssh-client package and use SCP.
```

sudo apt-get install openssh-client
scp <local file> <user>@<remote host>:<remote file>
scp <user>@<remote host>:<remote file> <local file>

```

---

### Post by p_quarles on 2008-01-23
> **ben22 said:**
> Hi,

I have been using WinSCP3 to transfer files via ssh - what SIMILAR program to you recommend to use on Ubuntu.

thx,
ben
Many FTP clients have support for SFTP (which is what WinSCP uses). Personally, I use Filezilla, but if you use the package manager to search for "ftp", you'll see a range of choices.

---

### Post by Bachstelze on 2008-01-23
> **Cypher said:**
> Install the openssh-client package and use SCP.
```

sudo apt-get install openssh-client
scp <local file> <user>@<remote host>:<remote file>
scp <user>@<remote host>:<remote file> <local file>

```

Maybe he wants something graphical... Then, using the SFTP subsystem, he can use a standard FTP client like FileZilla or gFTP. Konqueror can also do that and I *think* (not 100% sure) Nautilus too.

---

