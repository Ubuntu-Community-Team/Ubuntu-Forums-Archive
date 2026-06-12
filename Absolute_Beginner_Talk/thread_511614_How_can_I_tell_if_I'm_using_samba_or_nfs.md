---
title: "How can I tell if I'm using samba or nfs?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-07-28
I have an ubuntu computer on my windows network and I have been transfering files back and forth to my windows PC using winscp.  It's hard for me to remember everything that I did to finally get this to work.  I think I installed ssh, samba and nfs.  the rate of xfer between the pc is pretty slow.  I'm getting a max of approx. 2500KB/S which I suppose I could live with but it's pretty slow.  I tried to setup an ftp server which I heard is faster but I havent been successful in setting it up so far and I wanted to see if NFS is working or if i even have NFS installed.  I'm hoping that some one can assist me in determinig which file transfer method i'm using.  After I figure that out I would like to find out how to get faster xfer rates.

---

### Post by bbzbryce on 2007-07-28
> **videocheez said:**
> I have an ubuntu computer on my windows network and I have been transfering files back and forth to my windows PC using winscp.  It's hard for me to remember everything that I did to finally get this to work.  I think I installed ssh, samba and nfs.  the rate of xfer between the pc is pretty slow.  I'm getting a max of approx. 2500KB/S which I suppose I could live with but it's pretty slow.  I tried to setup an ftp server which I heard is faster but I havent been successful in setting it up so far and I wanted to see if NFS is working or if i even have NFS installed.  I'm hoping that some one can assist me in determinig which file transfer method i'm using.  After I figure that out I would like to find out how to get faster xfer rates.

If you're using scp that means your connecting through the ssh daemon thus it is neither smb nor NFS. You will lose a great deal of speed because of the encryption. For the fastest transfers connect with NFS, though it is the least secure as no authentication is required, besides the allowance of IP addresses.

From the scp man page:

> 
   scp copies files between hosts on a network.  It uses ssh(1) for data
     transfer, and uses the same authentication and provides the same security
     as ssh(1). 

---

