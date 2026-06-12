---
title: "Speed up Samba?"
date: 2007-01-17
forum: Apple PPC Users
---

### Post by terryeden on 2007-01-17
Afternoon all!

I'm trying to set up an old Rev C iMac 266MHz 158MB RAM as a file server using Samba.  Running Ubuntu 6.10 Alternative install for PPC.

My problem is that Samba performance sucks!  BWM shows peaks of 4000KBps which drops fairly regularly to around 3KBps!

I've stopped all non-essential services (including X) etc. I've tried running Xubuntu.  Nothing seems to help.  I've tested the cable and the receiving device - both are fine.  FTP has a sustained transfer rate of around 6000KBps.

I'm trying to stream from the iMac to Xbox Media Center.  My only option is to use SMB shares.

So - what's the magical command line switch to improve Samba's speed on this old hardware?  Are there any diagnostics I can do to see where the problem is?

Thanks

T

---

### Post by tagra123 on 2007-01-17
sudo apt-get install samba-doc

firefox usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html

From that page try enabling 
The socket option TCP_NODELAY is the one that seems to make the biggest single difference for most networks. 


In /etc/samba/smb.conf

change

#socket options = TCP_NODELAY

to

socket options = TCP_NODELAY

Different hardware can also affect speed.

---

