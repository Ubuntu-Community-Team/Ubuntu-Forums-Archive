---
title: "mount network drive"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by prem1er on 2008-04-03
Hi, I'm trying to mount a networked drive on my Ubuntu client machine from my Ubuntu server.  I know there are plenty of posts on this, but I'm trying to sift through them.  Does anyone have a good tutorial from the wiki of a link to another post to do this?  Thanks in advance.

---

### Post by Slushdoot on 2008-04-03
This should be good for setting NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

If you have Samba on the server you can use that too.: [https://help.ubuntu.com/community/SettingUpSamba?highlight=(Samba)#head-d0cf07ad854d6a463aa1ba9345600732832d47ef](https://help.ubuntu.com/community/SettingUpSamba?highlight=(Samba)#head-d0cf07ad854d6a463aa1ba9345600732832d47ef)

---

### Post by prem1er on 2008-04-03
I am currently using an Ubuntu machine as my client, but maybe will expand some windows machines on the same share.  Is it worth me setting up the Samba server now or should I just set up NFS and switch to Samba if/when I network the windows machines?

---

### Post by Slushdoot on 2008-04-03
If you only want to do it once Samba is the way to go. :)

---

