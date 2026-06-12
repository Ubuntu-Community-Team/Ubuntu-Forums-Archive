---
title: "Sharing Folders with NFS"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-11
I was looking for a simple guide to setting up sharing folders using NFS.   Nothing out there from what I can see.  Lots of clever things by people who know,  but nothing to the point in plain English.

I got the idea that setting up folder sharing was going to be easy with NFS and so I thought I would then have a go. I do not want to use Samba since I do not use Windows at all.

On each of four machines I created added a directory to the shared folders (System / Administration) and then selected NFS. I added both host names and IP addresses. Set the directory permissions and left it alone.

Looking in the /etc/exports file I can see the directory and the allowed computers for access.

Somewhere I read that I need to do some sort of edit on /etc/fstab but there are no clues as to what.

I wonder is there anything else I should do?  I think I am missing at least one step and probably more :(

Looking in Places / Network I get an icon for Windows Network appearing but nothing else.  Not using Windows I do not quite understand why that icon appears but also I do not understand why there is no icon for NFS.

---

### Post by skanchi on 2007-11-11
Steps written are correct. Entry in the '/etc/fstab' only requires, if you what them mounted at startup. You didn't mention about your network topology.

If you have direct link ( cross-cable) between NFS server and client, The client fails to mount the NFS directory reporting as 'RPC: timed out'. But, works if both are on LAN (using a switch or hub).

---

### Post by expatCM on 2007-11-11
thanks for the response ....  but I am still a bit confused .....

So I edit fstab on each machine to include the shared folder and that will be mounted on boot ...  fine.

I do not understand the significance of the NFS Server ...  I think this appears to be installed by default, do I need to do anything with it?

The topography is very simple, four pc's connected to a multi port router ....   could not be easier ..

In Places / Network, should I see an icon for NFS?

---

### Post by expatCM on 2007-11-12
and I just added the following line to fstab and then the system would not boot.  Commented it out and the system booted.  Can you tell me what is wrong with it?

/dev/hda3     /home/user/transfer    ext3    defaults        0       2

transfer is the shared directory.

---

### Post by expatCM on 2007-11-12
I have moved on and changed the line in fstab to the following

ga-m55s-s3:/dev/hda3    /home/user/Transfer    nfs rw,hard,intr 0 0

How do I know if the NFS share is mounted?  It does not appear with sudo fdisk -l or df -h

Based on the number of responses I get on this thread I guess there are a lot of people who do not know about NFS.  Perhaps it is not as simple as it is made out to be :)

---

