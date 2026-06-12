---
title: "FreeNAS guide?"
date: 2006-12-29
forum: BSD
---

### Post by crispy_420 on 2006-12-29
Does anyone know of a good and easy to user guide for FreeNAS?

I'm mainly looking for some help managing files, adding and deleting.

---

### Post by kd7swh on 2006-12-29
Novell has a FreeNAS install guide it the developer wiki:

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_FreeNAS](http://developer.novell.com/wiki/index.php/HOWTO:_Install_FreeNAS)

as far as file management i think FreeNAS uses samba. So you can just "connect to network server" or just enter SMB:// and the IP of the NAS in a browser.

---

### Post by crispy_420 on 2006-12-29
I actually came across that guide last night. It mainly looks like an install guide. That was no problem for me. I was able to access via the network to see my files as a network share and via ftp.

My problem is that I can add files just fine and I did to test if it was working. But from the same window that is open, I cannot delete my test files. 

I tried to google my issues and I only came up with install guides and vague howto's.

---

### Post by kd7swh on 2006-12-29
Is it a permissions issue? Maybe a .conf file that you could edit to give you read write access.

---

### Post by crispy_420 on 2006-12-29
No idea how to change permissions on remote server.

FreeNAS has no tools in it and I'm sure if there is a command line option to do it.

---

### Post by crispy_420 on 2006-12-29
OK, I think I found my solution.

I just found a little program called gFTP to manage my files and it works just perfectly for my needs. Ubuntu saves the day again. Now I can add many files at once and easily delete too. And as a bonus it is in the repos.

Thanks for the tips anyway. It turns out I didn't need a guide anyway, just needed to look at my problem a different way.

---

### Post by jac0117 on 2009-01-09
So how did you connect to freenas?  Just use the IP address of the server?  I'm having trouble with FreeNAS.  It works, but I have no idea how to add, create, delete files.

---

### Post by mips on 2009-01-09
[http://ubuntuforums.org/showthread.php?t=1005192](http://ubuntuforums.org/showthread.php?t=1005192)
[http://ubuntuforums.org/showthread.php?t=1025045](http://ubuntuforums.org/showthread.php?t=1025045)
[http://ubuntuforums.org/showthread.php?t=998490](http://ubuntuforums.org/showthread.php?t=998490)

Might find usefull info in those links.

---

### Post by dmizer on 2009-01-10
This thread is over two years old. I'm closing it so it can rest in peace.

Thank you :)

---

