---
title: "remount network drive that boots slower than ubuntu"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by asteinmetz on 2008-04-13
When I have to reboot all my systems (power failure or whatnot) my ubuntu box comes up faster than my NAS so the mount command doesn't connect the network drive.  running
**mount -a**
brings things up just fine once the NAS is visible again.

I have seen the messages that suggest creating a script and chron job to ping the IP and remount if needed.  Is that the "right" way?  It seems kludgy to me. 

Q1: Is there as system default setting that does that?

The weird thing (to this noob) is the desktop sees the drive as a samba share without mounting.  mount sets it up as an NFS share and once I mount it, the desktop shows both shares.  So I guess the samba share isn't linked to any mount point.  

Q2: Can I point the applications that are looking for the network drive to the samba share without having to mount it?

Thanks.

---

### Post by ofb on 2008-04-17
In my own experience so far you've got it right. NFS is still kludgy, whereas SMB is refined.

As for Q2, try it & report back. Might work -- you don't actually "mount" SMB shares in the Linux sense. SMB is deliberately the same thing as Microsoft Network Neighborhood.

NFS is the *nix style of mounting devices, but hasn't been refined for home user desktop use yet. It was designed for systems that stayed on. Hence you've got to run mount if the sharing system wasn't available when you booted, and there's also the nasty problem of file manager lockup when the sharing system shuts down before you do.

---

