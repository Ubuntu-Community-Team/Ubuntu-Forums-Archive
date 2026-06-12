---
title: "[SOLVED] how do i setup sharing between 2 ubuntu computers"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-27
title says it all
2 ubuntu ultimate 1.6 (gutsy) computers, i want them to be able to access the files on each other, but share one home directory.  i am using a linksys router, local IP is 192.168.1.1 comp #1 has 80GB hard drive, other one has a 100GB hard drive, and the one with an 80GB has a 1tb xternal usb hard drive and a printer plugged in, i want to be able to access everything from either computer



EDIT:
solved because i started using the "share using windows network (smb)" option rather than the "share on unix network (nfs)" i dunno why i have to use a windows network to do it, but hey whatever works right :/

---

### Post by steveneddy on 2008-01-27
Install Samba on both machines.

Right click the folder you want to share, click share Folder - choose Samba.

Go to Places --> Network

Browse your new share.

Easy :)

---

### Post by mortsahl on 2008-01-28
Samba will work ... but NFS is a lot faster.  Also, that doesn't answer his question of how both computers can share one /home directory ... don't know if you can do that, and if you can, it will slower than h*ll for the computer whose /home is remote.

---

### Post by antisocialist on 2008-01-28
> **mortsahl said:**
> Samba will work ... but NFS is a lot faster.  Also, that doesn't answer his question of how both computers can share one /home directory ... don't know if you can do that, and if you can, it will slower than h*ll for the computer whose /home is remote.
one of them can be slow as hell, i only use it to do some online things with flash
by default a linksys router will give you an IP of 192.168.1.1 but that doesnt seem to be working, so how do i find out what the host name is?

also, my router doesnt want to be logged on to (i go to 192.168.1.1in ff and it just shows loading for like 5 mins then gives an error) and i cant reset to factory defaults, as you can see my internet is working just fine as i am able to post this, i merely cant log in to my router

---

### Post by harrybazeegar on 2008-01-28
if both computers are ubuntu( or any linux for that matter ) you could set up ssh servers on both and use sftp to browse files on one computer from the other. 

I know that Konqerer supports sftp:/ , i am not sure about other browsers

---

### Post by louieb on 2008-01-28
> **harrybazeegar said:**
> if both computers are ubuntu( or any linux for that matter ) you could set up ssh servers on both ...
+1 Install **openssh-server** on both machines. Then open up places>connect to server> server type **ssh**. Once its setup  your other machine will appear in the file browser just like the local machine. 

NFS is harder to setup but once setup its easier to use. Just to get you started ssh is the way to go.

---

### Post by louieb on 2008-01-28
> **antisocialist said:**
> by default a linksys router will give you an IP of 192.168.1.1 but that doesnt seem to be working, ...

I sometimes have trouble logging into my router using wireless. Try a wireed connection. The other thing to try is use IP 10.0.0.1.  (thats the other common IP routers use).

---

