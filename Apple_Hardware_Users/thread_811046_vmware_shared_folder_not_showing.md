---
title: "vmware shared folder not showing"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by big-chip on 2008-05-28
Hi there,

I today just installed ubuntu in vmware fusion on my macbook. I have to say its all working as far as i know but there is one thing that seems to not be working. I want to set up a shared folder for my documents between os x and ubuntu. As far as i understand while ubuntu is up and running i click on the settings tab and under shard folders add a folder called something like "host" and point it to my home directory on os x. In theory this should give me a file:

/mnt/hgfs/host

that should have the contents of my home file on os x in it. However this file appears to not ever be created it doesn't show up in the file browser of if i look for it in terminal. 

Anyone else had this problem or know of a solution to it? any help or advice would be much appreciated im still a linux noob and still feel a bit lost.

cheers

chip
x

---

### Post by cyberdork33 on 2008-05-28
you are going to need to look at the vmware documentation on that one.

---

### Post by mfox on 2008-05-28
Have you installed VMware tools?  If those are not installed properly, you will not have the full functionality included with VMware Fusion, possibly including shared folders.  When I installed Ubuntu Hardy on my C2D mini through VMware, I read on one of the forums that you had to download an open source version of VMware Tools and compile them.  I found instructions on how to do this on this forum (I think it was a VMware forum), and successfully compiled and installed the tools. As a result, I have full functionality on my Hardy Heron installation, including movement of the cursor in and out of the VMware window, the ability to drag and drop files between Mac and Ubuntu, the ability to resize the Ubuntu window on the fly and the ability to add and view shared folders.

---

### Post by manna007 on 2008-05-29
Iam also faced same problem so plee...
=========================================
manna.....


a place you are knowing sports

[http://sports.com](http://sports.com)

---

### Post by mfox on 2008-05-29
[Here]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html") are the instructions for building VMware Tools from the open source binary and installing them on Ubuntu.  If you tried installing the tools the usual way and are missing some of the tools functional I described in the previous post, follow these instructions.

---

### Post by stueng on 2008-05-29
it might be /media/hgfs in Ubuntu btw

---

### Post by big-chip on 2008-05-29
> **mfox said:**
> [Here]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html") are the instructions for building VMware Tools from the open source binary and installing them on Ubuntu.  If you tried installing the tools the usual way and are missing some of the tools functional I described in the previous post, follow these instructions.
 
Awesome i read something about doing this after i posted here but it wasn't very clear as to what i had to do. Thats cleared the problem up no end and all is working well now. Also learn a couple of unix commands that may come in handy from doing it :)

---

