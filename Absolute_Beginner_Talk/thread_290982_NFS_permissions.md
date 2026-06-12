---
title: "NFS permissions"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by bduenskie on 2006-11-01
I have the following share setup through NFS:
/var/www 192.168.1.1/24(rw,no_root_squash,async,insecure)

I see I give "rw" privileges, but "rw" doesn't allow for the remote user to create folders, how can I give access to allow that?

---

### Post by DaveBorealis on 2006-11-01
Hello,

The remote user can save files but cannot create a folder in the same directory (or folder) in which the file was saved?  I've always been able to create new directories in any directory that I could save a file to.  Or have I misread your post?

Best regards,
Dave

---

### Post by bduenskie on 2006-11-02
Nope you haven't miss-read.  I'm able to create files within that folder, but unable to create folders.  I guess this is quite strange.

---

### Post by DaveBorealis on 2006-11-05
I've been waiting to see the solution...apparently nobody has any ideas.

bduenskie, how exactly are you trying to create the folders?  Are you using a file manager, such as Nautilus window, or trying by hand using a terminal or a virtual console?

Dave

---

### Post by PokerFacePenguin on 2008-06-21
> **bduenskie said:**
> I have the following share setup through NFS:
/var/www 192.168.1.1/24(rw,no_root_squash,async,insecure)

I see I give "rw" privileges, but "rw" doesn't allow for the remote user to create folders from the client, how can I give access to allow that?

I am having this same problem.  I can mount the nfs share from the nfs server on the client machine, but I cannot create folders.  I made the same username on the server and the client and put them both into a users group and chown -R root:users on the server side.  I went to the mount point "/media/networkbackups" on the client side and assigned the same permissions to that mount point file.  If I create a new folder from the server side inside the directory of the network mounted directory of the server, the permissions of the server directory show joe:joe while the permissions of the client side show an id that does not exist on the server (it shows the administrative id for both owner and group on the client side).  Is it necessary to run an LDAP server or NIS to get this working?

---

