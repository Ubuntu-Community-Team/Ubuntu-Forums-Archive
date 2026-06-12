---
title: "LAN working..... how to share a folder or file?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2007-01-08
i have connected two machines with a simple LAN. I can ping from either machine to the other.

How to share a file or folder?

How to share the Internet connection? This is the most vital for me.

Thanks in advance.

---

### Post by kj1h234lkj1234 on 2007-01-08
For sharing files across your LAN, you have 2 options:

[Samba](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

and

[NFS](http://ubuntuforums.org/showthread.php?t=249889)

If you are not worried about security on your network, NFS is much faster (easier to set up, file transfers are much faster as well).

Samba can be a pain in the butt, but it's the only way to share files between Windows and Linux.

As for sharing the internet connection, I am not sure how to do that the best way. Perhaps someone else can help you with that.

Good luck!

---

### Post by capitalistpiglet on 2007-01-08
what operating system does the other machine use?
If it uses linux then nfs or sshfs would we your best bet for sharing, if its a windows machine then samba. There are howto's for all three on the forums.

---

