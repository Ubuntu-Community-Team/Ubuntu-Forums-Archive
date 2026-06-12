---
title: "Connecting development server and desktop"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by fatphilthethird on 2007-03-24
Hi

Can someone advise on the best way to connect my desktop to an old box I've installed ubuntu server on? They're connected via my router, I've got apache & php working and can see a test page via the browser on my desktop. 

Now I need to set up file access and was wondering what's the simplest way of doing this? I've been playing around with vsftpd but I think that may be overkill; all I want is to give my desktop full permissions over the apache root folder.

Also, is what I'm doing secure? I'm sat behind a router/firewall so I assume so.

Any suggestions?

Thanks

Fat

---

### Post by gilgongo on 2007-03-25
There are several ways of doing this, but perhaps the most usual is to export what you want to have access to on the server as an NFS mount.  I'm not familar with NFS under Ubuntu, but I'm sure if you search around here you can get the info. Failing that, you can try setting up Samba, although there's not much of a point in that unless you plan to connect Windows machines to the server as well. In either case, you'll need to sort out the permissions, since the Apache stuff will be owned by root - you'll need to set the umask for the NFS export (or Samba mount) to access as root. 

Oh, and yes, you'll be secure as long as nobody from outside your network can get in to yours.

---

