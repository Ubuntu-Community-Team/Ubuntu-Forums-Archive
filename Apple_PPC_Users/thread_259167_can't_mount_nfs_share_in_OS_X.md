---
title: "can't mount nfs share in OS X"
date: 2006-09-17
forum: Apple PPC Users
---

### Post by brettfavre on 2006-09-17
I'm having trouble mounting an exported directory on my ubuntu box in OS X.

My exports file looks like this:

/home/brian 192.168.1./255.255.255.0(rw,async,insecure)

I've restarted the nfs server.  On the client end, I use the NFS Manager program to mount the share. I've had no success so far.  I did have this working in freeBSD.  Any ideas whats going on here?

---

### Post by ristosu on 2006-09-17
I'm not sure about this, but I would write 192.168.1.0/255.255.255.0.

On my RH9 PC, man mountd says that tcp_wrappers is used. If this is the case on your distro, then you should add 'mountd: 192.168.1.0/255.255.255.0' to '/etc/hosts.allow'. Or, if tcp_wrappers requires domain names, you could put your OS X host's IP address and name into '/etc/hosts', and use that name in '/etc/hosts.allow'.

---

### Post by brettfavre on 2006-09-17
Thanks, it was infact something to do with how I had the subnet mask set up.  For now ill just use a static IP.

---

### Post by brettfavre on 2006-09-17
Ok, here's my new issue.  I can't get the drive to mount with read/write.

Here is my updated exports file:

```
/home/brian mbp(rw,async,anonuid=1000,anongid=1000)
```

What happens, is the drive will in fact mount, but i get insufficient access privileges error when I try to write to the dir.  As you can see, I even mapped the client to my user id on the ubuntu server, and no luck.

---

### Post by ristosu on 2006-09-17
Maybe you are not root on your OS X machine. Try adding all_squash option to exports file.

---

### Post by brettfavre on 2006-09-18
That was it, thanks a million.

---

### Post by anders_gud on 2006-09-18
> **brettfavre said:**
> I'm having trouble mounting an exported directory on my ubuntu box in OS X.

My exports file looks like this:

/home/brian 192.168.1./255.255.255.0(rw,async,insecure)

I've restarted the nfs server.  On the client end, I use the NFS Manager program to mount the share. I've had no success so far.  I did have this working in freeBSD.  Any ideas whats going on here?

try:
mount -t nfs -o hard,intr -o -P server:/share/point /mount/point

-P option has to do with secure/insecure ports (BSD and linux plays different there...)

---

### Post by ghinch on 2008-03-10
> **brettfavre said:**
> Ok, here's my new issue.  I can't get the drive to mount with read/write.

Here is my updated exports file:

```
/home/brian mbp(rw,async,anonuid=1000,anongid=1000)
```

What happens, is the drive will in fact mount, but i get insufficient access privileges error when I try to write to the dir.  As you can see, I even mapped the client to my user id on the ubuntu server, and no luck.

I am having the same result, even after adding all_squash to the options. Here's my line:
```
/home/mediacenter 192.168.2.113(rw,async,anonuid=1000,anongid=1000,all_squash)
```

Anything I'm missing? I'm using the same program (NFS Manager) to do the mounting, any specific settings in that I should make sure of?

---

### Post by ristosu on 2008-03-10
I have no experience of NFS Manager, but it may have some option for selecting between r/o and r/w access.

Your (mediacenter's) uid on the Ubuntu server is 1000?

---

