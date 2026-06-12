---
title: "Remote File Sharing"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by othsy2k on 2007-08-03
Okay, I have Samba set up so my XP box can fileshare while I'm at home. I also went through the headache of getting TightVNC to work so I can see my desktop while I'm out and about (though the thing runs like my grandma when her arthritis is acting up). 

What I want to do now is access files remotely. Meaning while I'm out and about use my XP box to access my Ubuntu box at home for docs and media. Is this possible and how? 

Also, I have an external drive I'm tired of lugging around. Can I access this remotely if it's on the Linux box?

---

### Post by nexu56 on 2007-08-03
Just install ssh (sudo apt-get install ssh), then port forward port 22 from your modem/router to your home ubuntu box. Then you can connect to your ubuntu box from your xp box over sftp using filezilla or winscp.

---

### Post by othsy2k on 2007-08-03
Perfect. Thanks. Now I won't ever say "damn I wish I would have brought...." Can't believe it was that easy.

---

