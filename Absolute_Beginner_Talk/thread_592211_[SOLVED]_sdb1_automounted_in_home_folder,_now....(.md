---
title: "[SOLVED] sdb1 automounted in home folder, now....(Gutsy)"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by mandrill on 2007-10-26
have placed link on desktop, but want the drive icon instead of a folder icon - know the theory, but where  do I grab the drive icon from? and will it get rid of that damn little arrow?

also, i want to share that drive with my windows box, and my user name is the same on both machines....is all I have to do is share the drive and change the samba password to my universal password? (it shows unix user (me) and windows user (me) with a pre-allocated password that I cannot read) 

Any smartness you can share will be appreciated! Thanks is advance for the help!

---

### Post by Trebaruna on 2007-10-26
I believe that editing the properties of a link allows you to change the icon - just click on the icon in the properties window.

Also, to do it properly, you'd mount the drive in the /media/yourdrivehere structure. I believe drives mounted there will automatically show up on your desktop with drive icons, without arrows.

---

### Post by mandrill on 2007-10-26
> **Trebaruna said:**
> I believe that editing the properties of a link allows you to change the icon - just click on the icon in the properties window.

Also, to do it properly, you'd mount the drive in the /media/yourdrivehere structure. I believe drives mounted there will automatically show up on your desktop with drive icons, without
arrows.

Yes, I suppose I could then create a link in my home folder...however, to what directory would I migrate for the drive icon once i have accessed the properties portion of the link?

I have noticed that cd-rom drives mounted in media have pre-created links, with arrows, that do not automatically appear on desktop, no?

---

### Post by mandrill on 2007-10-26
> **Trebaruna said:**
> I believe that editing the properties of a link allows you to change the icon - just click on the icon in the properties window.

Also, to do it properly, you'd mount the drive in the /media/yourdrivehere structure. I believe drives mounted there will automatically show up on your desktop with drive icons, without arrows.

Quite so! I re-did it the way you described, and found it to be much more satisfactory - thank you!

---

