---
title: "Kmail--archive one folder"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-07-11
I'm about to transfer to a new computer, but I don't need to move all my emails. I've found the individual folders in /home/user/.kde/.../kmail/mail through Konquerer. But there are all kinds of index files and the like. I'm using maildir format.

Could someone please tell me what I need to archive, and if I'll be able to read the emails in something other than Kmail?

---

### Post by Jucato on 2006-07-11
If I'm not mistaken, the contents of the sub-folders that you create are found in ~/.kde/share/apps/kmail/mail/.inbox.directory
Take note of the . in .inbox.directory. It's a hidden folder. 

Hope that helps.

---

### Post by editrix on 2006-07-11
> **Fenyx said:**
> If I'm not mistaken, the contents of the sub-folders that you create are found in ~/.kde/share/apps/kmail/mail/.inbox.directory ...Hope that helps.

It's a start :-) Thanks.

I found three .directory folders. Trouble is, I've got about twenty kmail folders--for mailing lists, specific contacts, etc. And when I looked in these 3  .directory folders, they're empty.

Yuk! I tried just copying .kmail/mail to the new computer, and all the folders on the new computer are empty!

---

### Post by Jucato on 2006-07-11
Ok, that's weird. I've been able to move my ~/.kde/share/apps/kmail/mail contents around with no problem.

Unfortunately, I'm out of ideas. I've only recently started using KMail (or an e-mail client for that matter) and I'm still trying to learn these things.

---

### Post by editrix on 2006-07-11
> **Fenyx said:**
> Ok, that's weird. I've been able to move my ~/.kde/share/apps/kmail/mail contents around with no problem. 

Can I ask if you did anything other than copy the 
/kmail/mail folder to a different machine? And then, did you import the mail or just replace the /kmail/mail folder?

Any information's a help at this stage. Needless to say, I googled but didn't find anything useful.

---

