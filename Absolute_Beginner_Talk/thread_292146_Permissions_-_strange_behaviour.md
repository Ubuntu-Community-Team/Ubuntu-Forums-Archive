---
title: "Permissions - strange behaviour"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by ifo on 2006-11-03
I installed pure-ftp and pureadmin with root permissions. I did everything as described in installation guid. I could create users etc.

Then I started pureadmin and set the password and puredb file. I wanted to edit users and I get message permissions denied (accessing passwd file - did I mentioned that I'm still loged as root)! Ok something is wrong. So I renamed both files and restarted pureadmin. It found that both files are missing and offered to create them. I said Ok. The files were created but when I wanted to add a user I got error that somebody else is accessing the files and I can't write to them. Again restarted pureadmin and now I got the first error permissions denied.

PLEASE HELP!?

---

### Post by taurus on 2006-11-03
What do you mean when you said logged in a root?  Did you create a password for root and log in with it or did you log in with your username and password that you have created during the installing process?

---

### Post by Ecthelion on 2006-11-03
Maybe just rebooting could help...
Then it would be sure that no programs are opened that you don't see...

---

### Post by ifo on 2006-11-04
I created pass for root and logged in. I did the installation logged in as a root.

---

