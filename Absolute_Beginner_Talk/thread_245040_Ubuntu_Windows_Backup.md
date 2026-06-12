---
title: "Ubuntu Windows Backup"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-08-27
Hi,

I just backed up my system to a Windows machine the famlily uses as a file server. The backup stops at exactly 2 GB. I know that with the old FAT file systems that was a problem but the windows machine runs NTFS. What is keeping my files transfered from linux to windows limited to 2 GB. The folder on the remote machine is mapped to my computer and I used the sudo tar command to zip all my files on my machine. Is this something to do with using samba?

---

### Post by spin2cool on 2006-08-27
Not exactly an answer, but have you thought about using something rsync instead?

Once you get it set up, it'll just backup changed files (and can be setup to do so in the background without any intervention needed)

---

