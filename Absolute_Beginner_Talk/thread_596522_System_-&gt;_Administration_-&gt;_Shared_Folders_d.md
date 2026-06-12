---
title: "System -&gt; Administration -&gt; Shared Folders don't work .."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-29
I setup some folders to share in System -> Administation -> Shared Folders for sharing with other comptuers on my network LAN.  They can not see these folders -- neither my other Windows 2000 PC nor my other Gutsy PC can see these folders.  

Any ideas?

Thanks

Carl

---

### Post by Terc on 2007-10-29
have you restarted samba?  I noticed this issue also after creating my first share, I actually restarted my computer for an unrelated reason, when it came back up, the shares were available.

---

### Post by cwmoser on 2007-10-29
I modified /etc/samba/smb.conf with the file shares and I took your advice to restart via:
/etc/init.d/samba restart


So, how does the System -> Administration -> Shared Folders play in this?  It seems to be either not working or is something entirely different.

Carl

---

