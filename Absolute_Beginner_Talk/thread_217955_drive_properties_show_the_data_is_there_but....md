---
title: "drive properties show the data is there but..."
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Adragontattoo on 2006-07-17
Ok so I reinstalled Kubuntu due to breaking it and after moving over data and reinstalling I cant access the data.

/merlin I can access but /merlin/secured is inaccessible.  Any suggestions? 

Drive is showing that it has .9 Gb used so I know the files are there but I cant seem to figure out how to access the data. 


Any help would be greatly appreciated.

---

### Post by ProjectGod on 2006-07-17
sorry but you'll have give more details where did you move data ? onto another physical hard disk? did you do a clean install over the original?

---

### Post by Adragontattoo on 2006-07-17
the data was moved off of /home and onto another physical drive which was not reformated prior to reloading the OS and wiping / and /home/  

When I reloade Kubuntu I completely formated /home and /.

---

### Post by Adragontattoo on 2006-07-18
nudge

---

### Post by steve.horsley on 2006-07-18
I assume that /merlin is the mount point. What to you get when you do 
**ls -l /merlin**
I am wondering if the ownser of /merlin/secured is different to your new user id. If this is the case, /merlin/secured would show up with a numerical owner/group instead of a named one, and your normal user would be denied access (although root will have access - try **gksudo nautilus**.

If this isn't it, please tell us what you have done to try to get access, and in what way did it fail.

---

### Post by Adragontattoo on 2006-07-18
I have tried ls-l /merlin and the only thing that is showing is lost+found.

The properties is showing that there is 1gb of space used so the data is still there.  I am starting to wonder though if the data is just unretrievable.

I was wondering one thing though,  if I enable root as a login, would the data possibly show up then?

---

### Post by steve.horsley on 2006-07-18
You don't need to enable root. **sudo su** will get you a root prompt.

The existence of lost+found is a bad sign. This folder is created by fsck (File System ChecK, similar to chkdsk for DOS) if it finds errors in the file system. It is a  home for lost files - those for whom the meta-info like filename, owner and permissions is missing. I thnk you need to examine the contents to discover what they were.

---

