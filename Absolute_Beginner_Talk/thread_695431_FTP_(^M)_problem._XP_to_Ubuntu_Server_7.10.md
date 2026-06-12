---
title: "FTP (^M) problem. XP to Ubuntu Server 7.10"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by TheWhopper on 2008-02-13
Hello

On my server I'm running Ubuntu Server 7.10

On my client I'm running Windows XP

FTP software tried FileZilla and winSCP

***PROBLEM***
When I FTP files using either FTP software....from my XP machine, over to my Ubuntu server. For certain files, each line within the file will end with ^M.

I know this typically happens when FTPing a file from Windows over to a Linux without setting the transfer mode as binary. However, I've made sure binary is set on both FileZilla and winSCP before I FTP'd the file.

I know how to remove the caret M for each file by running a couple commands and I have a script to remove it from multiple files even within a subdirectories (however this breaks some files)

Any ideas what I'm doing wrong??? I know it's just me.....:lolflag:

---

### Post by njparton on 2008-02-15
Could I suggest that you use samba and map the shared drive in windows instead?

---

### Post by hyper_ch on 2008-02-15
you could locally mount it with sshfs and then just do a "local" cp.

---

