---
title: "Editing Files over Samba Without Sudo"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2006-12-06
I access my desktop's music files via Samba (it mounts at boot). Sometimes I want to write instead of just read (like to add files, edit tags, etc). However, sometimes I'll use programs (like amaroK) to do those, and it can't edit them without being root. I know I don't have read-only on the Samba share, because doing something like:

> sudo nautilus /music

lets me do anything I want (rename, move, delete, etc). How can I make it where I don't need to be root to write to it? I'm sure it's something wrong with my fstab file, so here's the relevant line:

> //192.168.1.150/music   /music          smbfs   uid=tony,gid=tony,guest,fmask=444,dmask=555,credentials=/etc/sambapass  0       0

---

### Post by tonyr1988 on 2006-12-07
I hate to bump (I promise this is the only time), but is there no way to accomplish this?

---

### Post by Iowan on 2006-12-07
I'll provide another bump for you...
Aside from that, I don't know if I can help much.  Who has write access to that folder (from smb.conf perspective)?

---

