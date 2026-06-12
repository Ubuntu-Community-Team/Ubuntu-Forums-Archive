---
title: "How do I install Ubuntu without losing Vista?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by tchase on 2007-05-10
How do I permanently install Ubuntu without losing Vista? Is there a way to run both OS's off of one computer. I'm still not postive I'm ready to make the final switch. If so, how do you do it (easily)? Thanks

---

### Post by Nekiruhs on 2007-05-10
You can make a new partition for Ubuntu and install it there. Vista will be untouched.  The way you do this is on the installer, when you get to the Partioning Screen, just choose resize and install. The slider will meausure the size of the Vista partition.  Btw. Welcome to Ubuntu.

---

### Post by Onesimus on 2007-05-10
The above suggestion does not work.

The only sure way is shrink the partition whilst still in Vista.  If it is unable to shrink as much as 
you would like, then remove the virtual memory (temporary) and other 'unmovable' files 
(e.g. the restore points).  Once the partition has been shrunk, then you can install Ubuntu.

When it comes to the paritioning during the install, choose the manual selection.

There are quite a few threads, regarding this.  I would search on those if you don't feel
confident.  

(I have successfully installed Ubuntu alongside Vista on my laptop, with no problems at all).

I would definitely RECOMMEND A BACK UP of your Vista files.  If you can't do the entire disk
make sure your important files. !!!

---

### Post by Nekiruhs on 2007-05-10
Sorry bout that, i forgot that only Vista can resize Vista partitions. Duh.

---

### Post by stmiller on 2007-05-10
Get the free gparted live cd. This lets you non-destructively resize NTFS (windows) partitions to create an unformatted partition for Linux.

---

### Post by Nekiruhs on 2007-05-10
> **stmiller said:**
> Get the free gparted live cd. This lets you non-destructively resize NTFS (windows) partitions to create an unformatted partition for Linux.

Again, there is something with Vista where even though it is NTFS, Vista will have problems if it doesn't resize it itself.

---

### Post by tchase on 2007-05-10
Vista came pre installed in my computer. How do I partition my disk after Vista was already installed? My computer did not come with disks containing drivers or the Vista OS, Compaq claims "You'll never need to reinstall with the restore point feature" Is there a way to install Ubuntu without reinstalling Vista? I'm looking for a relatively fool proof way to do this. It's a brand new laptop, and I don't want to mess it up.

Thanks

---

### Post by dstew on 2007-05-10
tchase:
Use the Vista Disk Management tool to shrink the Vista volume. It is in the My Computer --> Manage --> Storage --> Disk Management --> Shrink Volume. After that, you can install Ubuntu in the unallocated space.

---

### Post by jputman01 on 2007-05-10
> **Nekiruhs said:**
> Again, there is something with Vista where even though it is NTFS, Vista will have problems if it doesn't resize it itself.

i went thru this without any headaches, just make sure you read BEFORE you click!!

1. first thing is (while in vista) click the start menu, in the search bar type: disk management

2. then a new window will open asking you if you want to expand, shrink, etc. shrink to the correct size

3. insert your ubuntu cd, follow steps, when you get to the partition manager choose CUSTOM

4. you will see your windows partition (NTFS) with the size you shrank it to and the remaining should be unallocated space

5. create your ubuntu partition to your liking making sure you assign a "/" partition and a "swap" partition (FYI the thought I followed was making my swap partition twice the size of my ram, some people say 4 times the size but I went with just twice)

6. follow thru the rest of the installation

Also, after finishing this I had to add windows into my grub menu to be able to boot to vista, but we can tackle this after you get thru these steps (its really pretty easy).

P.S. PLEASE BURN YOUR VISTA RECOVERY DVD'S BEFORE STARTING THIS BECAUSE IF YOU BOUGHT YOUR COMPUTER WITH VISTA PRELOADED YOU MAY NOT HAVE RECOVERY DISCS TO USE, IT SAVED ME WITH MY FIRST INSTALL WHEN I SCREWED UP VISTA, if you bought vista seperately then you should already have these discs

---

### Post by Nekiruhs on 2007-05-10
Personally, I would call Compaq and ask to speak to someone in the upper ranks of Customer Service and politely yet forcefully request an OS cd atleast.  I know for a fact that Vista's restore point system is FAR from perfect.

---

### Post by jputman01 on 2007-05-10
> **Nekiruhs said:**
> Personally, I would call Compaq and ask to speak to someone in the upper ranks of Customer Service and politely yet forcefully request an OS cd atleast.  I know for a fact that Vista's restore point system is FAR from perfect.

that is what you burn, the OS recovery discs, the same ones you order from HP to my understanding

---

### Post by Nekiruhs on 2007-05-10
Apparently gateway does things differently then. Gateway shipped with no means of recovery and then charged me $20 for the restore CD.

---

### Post by tchase on 2007-05-10
what do you mean by: "assign a "/" partition and a "swap" partition"  ?

---

### Post by Nekiruhs on 2007-05-10
/ partition is like C:/ in Windows and Swap is a necessary extension of RAM, like window's pagefile

---

### Post by jputman01 on 2007-05-10
> **Nekiruhs said:**
> Apparently gateway does things differently then. Gateway shipped with no means of recovery and then charged me $20 for the restore CD.

they dont do it differently, HP also charges you for the recovery discs, but you can also burn your own from within vista itself. Say if you bought the computer from a retailer such as Office Depot, then the recovery discs wont come with it and I dont think they even carry them. Your options are call up HP, Gateway, or whoever and order them, the dvds run about $20 I believe OR you can burn your own from within Vista

I think we are saying the same thing just in different ways:)

---

### Post by jputman01 on 2007-05-10
> **tchase said:**
> what do you mean by: "assign a "/" partition and a "swap" partition"  ?

I returned your PM with a little more details but Nekiruhs hit it on the head for you! you are required a "/" and a "swap"

---

