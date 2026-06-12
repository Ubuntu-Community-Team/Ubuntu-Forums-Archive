---
title: "Noobix here"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by cmhill on 2007-03-30
I just installed Ubuntu yesterday and have most everything working so far except for a network share. I used to be connected to this share in XP by just mapping a drive to //172.16.1.9/biztech and giving it a username and password. I have tried several unsuccesful methods so far. The share is just a folder sitting on a SnapServer. Any suggestions?:confused: 


thanks in advance

---

### Post by jakev383 on 2007-03-30
> **cmhill said:**
> I just installed Ubuntu yesterday and have most everything working so far except for a network share. I used to be connected to this share in XP by just mapping a drive to //172.16.1.9/biztech and giving it a username and password. I have tried several unsuccesful methods so far. The share is just a folder sitting on a SnapServer. Any suggestions?:confused: 

If you connected to it using Win, try connecting to it as a SMB share in Ubuntu.

---

### Post by wpshooter on 2007-03-30
Have you installed either SAMBA and/or NTS in Ubuntu ?

---

### Post by cmhill on 2007-03-30
No, its just the base installation so far. Do both programs do basically the same thing? Which would you recommend I install?

PS. Im loving the Linux community so far!

---

### Post by cmhill on 2007-03-30
I am getting SMB4k from the add/remove porgrams applet right now. Ill let you know if I have any success.

---

### Post by cmhill on 2007-03-30
Ok, I can find the SNAP server if I search for that IP address in Smb4k, then expand and find the share I need access to, click on that and it tries to mount, and I get this.

Anonymous login successful
smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1

Im pretty sure, i need to specify an actual login to have fill access to this share though and I don't see a way to do that just yet. Maybe I havent gotten that far in this process yet?

---

