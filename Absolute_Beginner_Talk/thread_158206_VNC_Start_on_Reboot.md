---
title: "VNC Start on Reboot"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by s2h on 2006-04-10
I have Remote Desktop setup on my Ubuntu installation (Dapper) and everything works fine.  The problem is, the VNC application does not appear to run until I actually login.  This poses a problem as my machine is remote and after a reboot, I physically have to login to it to get the remote server running.  Is there any way to start VNC as a service so I can remotely access this box even if I haven't logged in (i.e. see the main login screen)?

Thanks

---

### Post by dlwofford on 2006-04-10
I have seen this also. A work around I did was set the graphical greeter to auto-login after 30 seconds as that user. This would start the VNC daemon and let me get access. 
Not a real answer to your question but a work around.

---

