---
title: "Dapper/Breezy Sharing Info"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Nameless on 2006-06-03
Hi all, 

I'm hoping I understand this correctly and if not perhaps I could be pointed in the right direction. 

I installed Dapper and it borked my sound and I didn't have time to correct it so I reinstalled Breezy and I'm going to install Dapper as a dual boot so I can slowly get myself converted and whatnot. 

I want to be able to boot into either and share programs/files/themes/customizations and the like.  To do this, is the /home directory the only directory that I will need share between the two?  Or will I need to share /etc or /var as well?  

As a note: I intend to make a new partition and move my /home directory to it so that it will be available and not copied over if I bork something else. 

Thanks!

---

### Post by Sirkent on 2006-06-03
This may not be practical! You can probably share your per-user configuration settings without too much difficulty, but ubuntu's package management system (aptitude) keeps a record of what it has installed, so both installations would need to be almost completely in synch for you to be able to share directories between them. This would mean you'd have to install them both seperately and then share them later. I don't even want to think about the difficulties this would entail.

---

