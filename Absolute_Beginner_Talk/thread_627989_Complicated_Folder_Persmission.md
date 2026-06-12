---
title: "Complicated Folder Persmission"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by greavr on 2007-11-30
Hi Everyone,

We are currently in the process of switching to an linux back-office system from the ever playful windows.

Im setting up the central file share folder however im stuck on how to arrange a folder share.

What I need to be able to do is allow users from different departments to access only specific folders with another departments network shared area.

For example I have an IT_DEPT and HR_DEPT folder, HR can not access the IT_DEPT folder and vice-verse. However HR make a folder within HR_DEPT which they need one member of the IT team to look at. What makes this more complicated is that the IT user should not be able to open or view any other files within the HR_DEPT folder, just the one they are supposed to access.

Is this sort of tunnelling possible if so how would it work.

Thanks for your help on this, I really want to get this going and show just how great linux can be.
:-s
Rick

---

### Post by approaching on 2007-11-30
i haven't done this before, but it looks like some groups are in order. you can create several groups, add each dept to the groups, and give those groups specific permissions over those folders.

---

