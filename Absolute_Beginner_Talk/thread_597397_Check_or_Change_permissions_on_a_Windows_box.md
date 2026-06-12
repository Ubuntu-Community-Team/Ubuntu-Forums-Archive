---
title: "Check or Change permissions on a Windows box"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by sknox on 2007-10-30
I'm able to mount a Windows drive and to write files there, no problem.

What I need to be able to do is to look at folders (this is on a Windows web server) and administer rights there. I need to be able to add a user to a folder, remove a user, and simply see a list of the owners on a particular folder on that Windows server.

From Windows I was able to look at the Permissions of the folder and do all this. From Permissions via smb all I get is "unknown" with no ability to change permissions.

I am not allowed to RDP into this box. The system engineers are telling me to run VMWare and just run an instance of Windows. That will work, but I'm trying to be as Windows-free as possible.

Is there anything I can do?

-= Skip =-

---

### Post by Jaco Du Toit on 2007-10-31
You can try a linux command line program called smbclient , though using it to change file and folder permissions is dependent on the actual server setup. Unfortunately that's all the help I can give as I have never actually tried it myself. ;-)

---

### Post by sknox on 2007-10-31
I appreciate the reply, but that doesn't really do the job for me. It doesn't let me see a list of owners and their current settings, which I need in order to know if something needs to be changed.

Anyone else? I would have thought lots of people would have the need to administer a Windows server from a Linux platform. Yeah, I know: RDP.  But that avenue is closed by management, claiming security issues. They don't want to give me access to the whole machine, only to the wwwroot branch.

-= Skip =-

---

