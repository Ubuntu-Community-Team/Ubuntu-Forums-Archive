---
title: "Configuring Samba for anonymous access???"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-03-18
How do i configure samba to allow anonymous access?

---

### Post by Stebalien on 2007-03-18
Follow the instructions at [ How to share public folders with read/write permissions (Authentication=No)]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29") or [ How to share public folders with read only permission (Authentication=No)]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29")

---

### Post by islander_810 on 2007-03-20
Well, that sort of answers my question. But the probs here are, i have to change the permissions manually of all the folders that i wish to share and then add them to the file.  This is to be done for every folder i share. Isn't there an easier way??

---

### Post by somebodycr on 2007-10-15
Well... for me it worked just by changing

;  security = user

to

security = share

in /etc/samba/smb.conf

and then restarting samba with 

sudo /etc/init.d/samba restart

:)

---

