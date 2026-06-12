---
title: "Is Samba the only one ?"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by toships on 2005-10-16
Hi all,

I have successfully set up Samba for my home network. I wanted to know if there are only two machines in my network and I need a samba-like service (basically access some folders from different comp), is samba the only one?

Just asking.
Using Breezy.

Thanks.

---

### Post by wylfing on 2005-10-17
If one or both of these computers run Windows, then yes Samba is the only thing that's going to let them talk. On the other hand, if both computers run Linux, I would recommend *against* Samba.

For shared directories, use NFS. For shared printers, use CUPS.

NFS is surprisingly easy to get up and running. Do some Googling to find out how. One thing I can tell you, however, is when given a choice of which NFS to use (kernel module or daemon), choose the daemon. I'm pretty sure the packages nfs-user-server and nfs-common are the ones you need.

---

### Post by patrick295767 on 2005-10-17
[QUOTE=wylfing]If one or both of these computers run Windows, then yes Samba is the only thing that's going to let them talk. On the other hand, if both computers run Linux, I would recommend *against* Samba.

For shared directories, use NFS. For shared printers, use CUPS.

NFS is surprisingly easy to get up and running. Do some Googling to find out how. One thing I can tell you, however, is when given a choice of which NFS to use (kernel module or daemon), choose the daemon. I'm pretty sure the packages nfs-user-server and nfs-common are the ones you need.[/QUOTE]


I wish you could help me to share my folders and printer on the samba network.

I am stucked with permissions ! no users can mount my shared folders under samba ...

Also I wish to share folders and cannot find anything in rox menu saying " SHARE..."

thanks a lot 

I looked also in ubuntu guide but not big success 

(Maybe I guess I could ask you via gaim ... )


pat'

---

### Post by patrick295767 on 2005-10-17
I tried to add a file in the /root/ wiht .smbpasswd and so on like explained but 
still not working for regular users ... 
I wihs ot have some help to enable users to mount their smb_user folder ...

How to share a folder with rox or xterm only ??

(no nautilus, only fvwm)

---

### Post by wylfing on 2005-10-17
patrick295767, you are hijacking the thread. No one is going to see your problem because it's "hidden" here. Please start a new thread and ask for help there, so that everyone can see what problems you're having. (I might help too :) ).

---

### Post by patrick295767 on 2005-10-17
[QUOTE=wylfing]patrick295767, you are hijacking the thread. No one is going to see your problem because it's "hidden" here. Please start a new thread and ask for help there, so that everyone can see what problems you're having. (I might help too :) ).[/QUOTE]

Ok !! Thx, I'll explain my prob of permissions ...

---

