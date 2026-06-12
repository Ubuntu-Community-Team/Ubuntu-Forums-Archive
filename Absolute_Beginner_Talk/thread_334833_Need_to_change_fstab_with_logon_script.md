---
title: "Need to change fstab with logon script"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by tracyapotter on 2007-01-09
Hello,

The question:  Can I use a login script to swap out customized fstabs depending on the user logging in?

The background:  I am runnig a peer-to-peer Linux/XP office network.   All shares are on FAT32 partitions regardless of whether the box is Linux or Windows.

_Samba is working perfectly_.  This is not that kind of problem.

When you run Samba, file previews are disabled (my jpeg picture is an icon, not a thumbnail).  I like previews, so mounting in fstab was the way to go.

After the holidays, one OS or both updated and now my /media mounts have an oddness that require me to use a uid=XXXX to make them work properly.  Believe me, I tried everything  on this forum and others, but something in one of the OSs changed and left me with this problem.  However, I have multiple users per computer that I do not want to have access to the same folders.

What I want to know is if I can have a script change out fstab files or lines depending on who logs in.

I.E.
UID=1000 gets a fstab with these lines:
//pwrconsrvr1/Accel	/media/Accel	smbfs	credentials=/root/.smbcredentials,uid=1000	0	0
//pwrconsrvr1/Gen_Resource	/media/GenResources	smbfs	credentials=/root/.smbcredentials,uid=1000	0	0
//pwrconsrvr1/Projects	/media/Projects	smbfs	credentials=/root/.smbcredentials,uid=1000	0	0
//pwrconsrvr1/Software	/media/Software	smbfs	credentials=/root/.smbcredentials,uid=1000	0	0
[COLOR="Orange"]//pwrconsrvr1/TAPotter	/media/TAPotter	smbfs	credentials=/root/.smbcredentials,uid=1000	0	0[/COLOR]

UID=1002 gets:
//pwrconsrvr1/Accel	/media/Accel	smbfs	credentials=/root/.smbcredentials,uid=1002	0	0
//pwrconsrvr1/Gen_Resource	/media/GenResources	smbfs	credentials=/root/.smbcredentials,uid=1002	0	0
//pwrconsrvr1/Projects	/media/Projects	smbfs	credentials=/root/.smbcredentials,uid=1002	0	0
//pwrconsrvr1/Software	/media/Software	smbfs	credentials=/root/.smbcredentials,uid=1002	0	0

and UID=1001 doesn't have these lines at all

By the way, gid=xxxx doesn't help because the XP share doesn't care (fat32)

I know I am being picky about seeing the thumbnails, but it sure has been another interesting  trip down the education highway.

TA Potter

---

### Post by bodhi.zazen on 2007-01-09
I would add all those mounts to fstab with uid=xxx, gid=yyy, and umask=007 or umask=077

umask sets permissions at mount so the propper umask restrict permissions to either user only (077) or user + group (007)

See either man mount or here:

[http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

HTH 8)

---

### Post by tracyapotter on 2007-01-09
Thank you, already been there.

The problem with setting things in fstab is that I do not want one of the users to even be in the Samba workgroup.  Group is  a linux thing is it not.  So my GuestUser is not included in my CompanyGroup, but I do not know how to have it not included in the SAMBA workgroup.

As it stands, while the /media mounts fine, I get "cannot change permission errors" unless I specify uid=xxxx.  If my GuestUser has any Linux brains at all, he can still Samba to the XP shares because the Samba Users tab is always blank (not permanently adding)

---

