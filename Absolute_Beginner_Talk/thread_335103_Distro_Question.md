---
title: "Distro Question"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by marcusgleason on 2007-01-09
I currently have a dual booted computer XP/Ubuntu.  I have the Ubuntu half partitioned three ways: swap, root, /home.  I want to install DreamLinux, but was wondering if I could leave the /home partition so that DreamLinux could use it.  DreamLinux is a Debian based distro like Ubuntu.  I really just don't want to erase my /home partition and start over.  I'm sure I would have to mount the partition once DreamLinux is loaded, but it should read it and write to it correct?

---

### Post by doobit on 2007-01-09
> **marcusgleason said:**
> I currently have a dual booted computer XP/Ubuntu.  I have the Ubuntu half partitioned three ways: swap, root, /home.  I want to install DreamLinux, but was wondering if I could leave the /home partition so that DreamLinux could use it.  DreamLinux is a Debian based distro like Ubuntu.  I really just don't want to erase my /home partition and start over.  I'm sure I would have to mount the partition once DreamLinux is loaded, but it should read it and write to it correct?

During the install, just label the partition /home again, but don't format it. Everything should work correctly.

---

### Post by marcusgleason on 2007-01-09
That's what I thought.  Thanks for your reply.  The reason I am going to DreamLinux is because they released a Multimedia Edition which is supposed to be pretty cool.  That and it has an NTFS writer built into the distro.  If you haven't check out DreamLinux yet, I would suggest at least running the Live CD and give it a go.  It's got a lot of good things in there.

---

### Post by rioghal on 2007-01-09
Wouldn't the apps he uses in Ubuntu need to be the same exact version of the apps in Dreamlinux? I would think he would get an error or two by using config files from one version in another version of an app. What would happen if app1 (Ubuntu) used a config file, then app2 (Dreamlinux) used that config file and changed something that app1 (Ubuntu) wasn't happy with when it uses that config file again? Is this not a worry in Linux?

---

### Post by Praxicoide on 2007-01-09
I really want to try that distro out. I might, after I solve my EVDO problem.

---

### Post by doobit on 2007-01-10
> **rioghal said:**
> Wouldn't the apps he uses in Ubuntu need to be the same exact version of the apps in Dreamlinux? I would think he would get an error or two by using config files from one version in another version of an app. What would happen if app1 (Ubuntu) used a config file, then app2 (Dreamlinux) used that config file and changed something that app1 (Ubuntu) wasn't happy with when it uses that config file again? Is this not a worry in Linux?

Most apps will check for version compatibility. There might possbly be an issue if the old config file is overwritten. However, I have done this with other distros and not experienced a problem. It actually had some benefits when the same apps were updated in the other distro.

---

