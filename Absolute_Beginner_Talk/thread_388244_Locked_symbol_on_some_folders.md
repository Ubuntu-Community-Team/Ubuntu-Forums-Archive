---
title: "Locked symbol on some folders"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-03-19
I'm dual-booting Dapper and XP Home.

I can access my windows folders from the desktop, but some of the folders have a padlock icon. These are in My Docs, and I can open and read them OK. So why the "locked" icon? And why just some of the folders? :confused: 

TIA.

---

### Post by eljalill on 2007-03-19
The padlock emblem means, that they have restricted access, and mostly implies, that you cannot delete/change them. I have no clue, why the access to the files in your docs might be restricted, but you can see in the properties who the owner and what the access status is, and in case you can write on your windows partition, you could try to change the access with sudo chown and sudo chmod.

---

