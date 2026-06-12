---
title: "5 + users Samba Issues. Fiesty Desktop"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by chrisdoesloans on 2007-06-07
Hello-

I'm puting ubuntu Fiesty Fawn Desktop in my office.  I want to be able to have 5+ users sharing data, and the folks at microsoft made XP such that only 5 connections...anyway.  Enough compliaining.

The premise is that I want to have 12-15 people connecting to a fileserver that can be mapped as a drive to various user's computers.  I want to have them be able to print, if need be, but printing isn't as important as filesharing, etc.  

I've successfully put ubuntu desktop on my system.   I would like to stick wiith a gui if possible, for the itme being, but if it's not possible, I still need to get this done.  How to get the command line?  How do I install packages?  I want this done, up and sharring tomorrow.

Please let me know.

---

### Post by Fitzy_oz on 2007-06-07
> **chrisdoesloans said:**
> Hello-

I'm puting ubuntu Fiesty Fawn Desktop in my office.  I want to be able to have 5+ users sharing data, and the folks at microsoft made XP such that only 5 connections...anyway.  Enough compliaining.

The premise is that I want to have 12-15 people connecting to a fileserver that can be mapped as a drive to various user's computers.  I want to have them be able to print, if need be, but printing isn't as important as filesharing, etc.  

I've successfully put ubuntu desktop on my system.   I would like to stick wiith a gui if possible, for the itme being, but if it's not possible, I still need to get this done.  How to get the command line?  How do I install packages?  I want this done, up and sharring tomorrow.

Please let me know.

Hi,
It's under the menu item  System -> Administration -> Shared Folders,

After which you can select whether NFS (Linux kernel File Sharing) or SMB windows filesharing is enabled.  Select SMB obviously and then share the folders you wish to via this wizard like interface, you can also right click on the folders in Nautilus just like you would in windows.  

If you wish to delve into it further you can, it can be setup as an NT4 style domain controller as well as a wins server, you can configure it for User authentication and log on scripts.

---

