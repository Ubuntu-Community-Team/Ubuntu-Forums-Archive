---
title: "using smb connections at command line"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by aws910 on 2007-05-31
2-month ubuntu newbie here.  

So I installed Quickbooks Pro 99 using WINE... was pretty proud of myself, it works ok.

My problem is that I'm accessing Quickbooks files on the network.  The system of WINE won't(apparently) let me access SMB shares that I'm connected to(using Places -> Connect to server).  Tried to create a symbolic link to the share(copying the location from the address bar) and it comes back at me saying "no such file or directory".

As a workaround, I used smbmount to mount it in my filesystem, then symlinked the mount in wine's "drive_c".  This setup was problematic because I had to use sudo to get anything to work properly.  I even had to use sudo to run wine, so that it would have the privs to write to the mounted share (chown and chmod yielded no results for me here).  The program doesn't run 100%, though, and I suspect it's running into a lot of privilege problems.  If I could find an easier way to read/write these files(mounting without sudo) I think things would work more smoothly, but this is where my knowledge ends.  

My biggest problem is this:  I don't understand where the links are stored, or how they work, when I map a drive using " Places -> Connect to server".  How can I access these links from a command prompt?

Sorry if it seems like I asked twenty questions about twenty different things.  I appreciate all the help everyone has given me here.

edit: I also tried locating the directory in file browser, right-clicking it, and selecting "make link".  it said "Error Unsupported operation while creating a link to "smb://domain.../qb""

---

### Post by xela321 on 2007-05-31
The first thing to know is that smbmount is kinda of a wrapper for the regular mount command.  Try mounting the samba share with this:

```
sudo mount -t smbfs -o username=**yoursambausername**,password=**yoursambapassword**,uid=**yourlinuxusername**,gid=**yourlinuxusername ** //sambaserver/path/to/share /path/to/mount/point
```

That should all be on one line.  There should not be any space between the 'u' in username and the 'e' in yourlinuxusername.  The command should make the mount point have the same ownership as other things in your home directory (yourlinuxusername:yourlinuxusername)

Cheers

---

