---
title: "Searching network storage"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-09-21
I have an SSH server running on an other machine, Is there any way of searching the hard drive using nautilus.

Even better would be a music player which can get its library from a network device.

Thanks

J

---

### Post by benfindlay on 2006-09-21
I've been looking for a music player that allows you to set a remote location as its library for a while now without any luck. hopefully someone else will know however

---

### Post by puelly on 2006-09-22
> **jd65pl said:**
> I have an SSH server running on an other machine, Is there any way of searching the hard drive using nautilus.

Even better would be a music player which can get its library from a network device.

Thanks

J

Depends on what music player that you are using.  One method could be to install SAMBA on your linux box and map the drive that stores your music on the windows PC.  Once the drive is mapped, you should be able to access its information easily from windows.

---

### Post by jd65pl on 2006-09-23
I'm not sure I ever mentioned windows as both the server and client are Linux. The only issue being that I cannot search the network storage!

J

---

### Post by wildseven on 2006-09-23
can't you remote desktop instead of ssh so u can use gui isntead of terminal? this way you can use nautilus can't you?

---

### Post by jd65pl on 2006-09-23
I'm happy with SSH. The server is NOT ubuntu nor is it capable of running it, It is works as a file server just fine. 

I am able to browse the hard drive attached to it but not search them using nautilus in the ubuntu client. Is there a solution to this which doesn't involve changing the method of file transfer.

J

---

### Post by jd65pl on 2006-09-27
Hey I fixed this issue by using sshfs which enables one to mount an ssh network resource.

---

