---
title: "MAC OS X FILE Permission"
date: 2009-03-03
forum: Apple Hardware Users
---

### Post by amb1s1 on 2009-03-03
I installed Ubuntu using boot-camp like a month ago. Now mac os x is not booting up. This has northing to do with ubuntu. I can see the MAC HD and I able to navigate throughout some of the folders, but some of the most important folder are mark with an X. When I try to opened it, I get:
You do not have the permissions necessary to view the contents of "Documents"
Is there a way to change permission using my MAC OS X Username and password from Ubuntu? I want to do this because I will like to do a backup from Ubuntu. Thanks

I have a Imac Intel using Ubuntu 8.10

---

### Post by cyberdork33 on 2009-03-03
well, let's review the problem and we might be able to help. What does the Mac do when you turn it on? Does it go directly to Ubuntu? Do you have refit? Does holding 'alt' during bootup make the boot selector appear?

If you want to access the files belonging to a different user (at least that is how your Ubuntu system sees them) then you can use root permissions (which override user permissions).

Open two nautilus windows by doing ALT+F2 and running the command "gksudo nautilus". You can then navigate to the Mac folders in one window, and navigate to your backup location in the other and drag files between them. Once they are copied, you can change the permissions on the files within Ubuntu.

---

### Post by amb1s1 on 2009-03-04
I have refit and when I choose mac os partition it try to boot but it shuts down after couple of second.

---

### Post by cyberdork33 on 2009-03-04
> **amb1s1 said:**
> I have refit and when I choose mac os partition it try to boot but it shuts down after couple of second.
have you tried booting the Leopard install disc and using Disk Utility to Repair?

---

