---
title: "How do I prevent having to put the CD in when I do an apt-get install?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by smithwk2 on 2008-02-29
How do I prevent having to put the CD in when I do an apt-get install?  Thanks in advance for the help.

Wayne

---

### Post by dondad on 2008-02-29
Go to software sources in the admin menu and uncheck the cd on the first page.

---

### Post by seventhc on 2008-02-29
go to *System>Administration>Software Sources* and uncheck  the CD option, you should see it near the bottom.

---

### Post by acsworrell on 2008-02-29
In your Synaptic sources list, just uncheck the box referring to the CD as a source. It should be on the first tab.

---

### Post by smithwk2 on 2008-02-29
dondad:

Thanks for the help!!  That did it!!  Have a good day.

Wayne

---

### Post by Oldsoldier2003 on 2008-02-29
> **seventhc said:**
> go to *System>Administration>Software Sources* and uncheck  the CD option, you should see it near the bottom.

And for those that to work on a remote server you can edit  /etc/apt/sources.list and comment out the line for Deb CD

---

