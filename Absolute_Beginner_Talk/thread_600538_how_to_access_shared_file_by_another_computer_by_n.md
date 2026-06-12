---
title: "how to access shared file by another computer by nfs"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-02
i have one computer on the network which has enabled smb and nfs. there are two folders , let's say folder1 and folder2, to be shared to the network. i have right-clicked them --- share folder -- chosen windows network (smb)/ unix network (nfs). but how to other computers (ubuntu 7.10, xubuntu 7.10, xubuntu 6.06) access them?

---

### Post by afeasfaerw23231233 on 2007-11-02
bump...

---

### Post by afeasfaerw23231233 on 2007-11-02
bumpbump

---

### Post by afeasfaerw23231233 on 2007-11-02
BUMP! why ''bump'' no longer useful?

---

### Post by quinnten83 on 2008-01-27
If you use them too often, people will start ignoring you.
I use SSH, I am also looking for intructions on how to NFS (that's how i came by this thread).
You can install ssh:

sudo apt-get install ssh

after installation you can access your the other computer by typing

ssh [email]username@ip.of.the.pc[/email]

where username is a valid username on the computer to be accessed (not sure about this one,, Ie only used the admin account so far) and ip.of.the.pc is the ip of the pc you need to access. 

If I get more information on NFS and I remember, I will post on this thread, although you've probably long gone figured out what you need to do by googling...

---

### Post by mortsahl on 2008-01-27
For NFS see

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

(I have nothing to do with that site, just found it more use than Ubuntu wiki when I was trying to set NFS)

---

