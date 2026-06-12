---
title: "Netatalk + guest access"
date: 2009-04-10
forum: Apple Hardware Users
---

### Post by wesg on 2009-04-10
Hi everyone,
I'm preparing to build my Ubuntu server, and have a quick question. I'm glad I found these forums!

I'm testing a ubuntu installation on my MacBook with Parallels, and I'm trying to get netatalk working properly with guest access. I've been able to set it up with my home folder, but guest access doesn't work. 

What settings do I need to change to enable this feature and how can I configure folders for new shared mounts?

---

### Post by cyberdork33 on 2009-04-10
> **wesg said:**
> Hi everyone,
I'm preparing to build my Ubuntu server, and have a quick question. I'm glad I found these forums!

I'm testing a ubuntu installation on my MacBook with Parallels, and I'm trying to get netatalk working properly with guest access. I've been able to set it up with my home folder, but guest access doesn't work. 

What settings do I need to change to enable this feature and how can I configure folders for new shared mounts?
what issue are you encountering? can you even connect to the share? I think that the user permissions on the files are respected over netatalk, so the file owner will need to allow access to guest users for that to work.

---

### Post by wesg on 2009-04-10
I can connect via Ubuntu user name and password to the home folder, but the guest share fails to connect. The folder I'm hoping to use has the permissions drwxr-xr-x. I'll try making it 777 and see what happens.

Also, this is the line I'm hoping to use for guest access inside AppleVolumes.

~/media "Media" allow:guest cnidscheme:cdb

---

### Post by wesg on 2009-04-10
Found the problem. I didn't actually have guest access turned on in afpd.conf. Problem solved!

---

