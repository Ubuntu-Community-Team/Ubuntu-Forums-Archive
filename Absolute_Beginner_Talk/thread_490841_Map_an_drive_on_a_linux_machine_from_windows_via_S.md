---
title: "Map an drive on a linux machine from windows via SSH?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-07-02
I'm sure this must be possible, what would be the easiest way to do this?

---

### Post by rillip on 2007-07-02
Let me make sure I understand the question, you want to map a drive on a computer running Linux as it's OS as a network drive on a Windows computer.  You have ssh access to the Linux box.  Is that correct?

If it is, I don't think this is doable unless the drive is something Windows can read, such as ext3 or ntfs.  Even then it'd probably be difficult.

Your best bet is probaby just to set up Samba and share it like that.

---

### Post by eternalsword on 2007-07-03
you would need to set up samba on the remote linux machine and then when sshing port forward 139 to the local windows machine and access the share via //localhost  you will however need to disable file sharing on the windows machine prior.  

Or you could try following this guide [http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php) which uses a virtual ethernet adapter running on loopback.  You would port forward then to the virtual ethernet as opposed to localhost, thus allowing the windows machine to maintain it's current filesharing capabilities.

if all you need is file access, you could look into winscp at [http://winscp.net](http://winscp.net)

---

