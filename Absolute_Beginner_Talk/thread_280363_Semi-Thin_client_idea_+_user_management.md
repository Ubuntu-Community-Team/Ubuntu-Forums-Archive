---
title: "Semi-Thin client idea + user management"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by ZiRo on 2006-10-19
I gather it is possible to mount files on seperate machines. e.g. I could mount my /home/ folder on a seperate ubuntu machine?

Am I correct?

If so, what would prevent the mounting of bin and config files in this manner too?

So any ubuntu machines on a network could potentially take all configuration and executable data from a central location, essentially logging onto the same data, on any machine on the network.

Possible?

Just to clarify - I'm not talking full thin client here, i'm talking config and bin files, not loading the kernel over network.

Also, is there any way to allow applications to be deployed by one accessable/installed only on their account?

---

### Post by Marsolin on 2006-10-19
I've never tried anything like that, but you can mount smb shares, so I would assume you could have fstab use that for one of the base directories. The potential problem that would prevent it is if the location you are trying to mount to needs to be called before Samba gets setup and connected. I'm not sure how that goes in the boot order.

---

### Post by ZiRo on 2006-10-19
I understood that you could mount "folders" e.g. /etc/ on external machines..

---

