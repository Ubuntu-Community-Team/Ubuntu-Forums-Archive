---
title: "Problem with OpenOffice launchers (Feisty)"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by petersjm on 2007-05-14
Hi guys,

I've scanned through the previously posted threads on this topic, but nothing helps me out. I've installed OpenOffice on Feisty (Kubuntu, if it makes a difference) but the usual "openoffice.org2.2-writer" command doesn't work. I've set up a link to /opt/openoffice.org2.2/program/swriter so I can just type "swriter" to get Writer to load (and set a launch pointing to the same link, but I'm not happy that I have to do this. Maybe it's just me...

Does anyone know why simply typing openoffice.org2.2-writer doesn't work? (I know typing swriter is shorter, but I'm used to doing it the other way and I don't like change LOL :p )

Oh, one more thing, I'm convinced I completely removed 2.0 and 2.1 in the past when upgrading, but if I right-click a document and select Open With > it still gives those two options, but if I select one of them it says cannot find executable...

Can any one offer any help? (in my best "Chucky" voice) I'll be your best friend till the end... :D

---

### Post by RSingh on 2007-05-14
Did typing "openoffice.org2.2-writer" work before, just asking??

---

### Post by steve.horsley on 2007-05-14
I thiink that your problem is that "openoffice.org2.2-writer" is not the name of the executable but of the launcher description. The instructions below are for Ubuntu but there must be a very close equivalent in Kubuntu.

Right-click your menu and choose Edit Menus. Open the launcher for OpenOffice (a different launcher for each doc-type), select the Properties and change the Command to:
**/opt/openoffice.org2.2/program/soffice -writer %U**
This (I think) relies on leavinf fthe original OOo installed, and just modifies the launchers that the original OOo package installs.

P.S. the at the end, **%U** may well be a nautilus thing (it is only the executable path that I changed - the **-writer %U** was there before). You will have to use the K menu method of representing the filename of course.

---

### Post by petersjm on 2007-05-15
> **RSingh said:**
> Did typing "openoffice.org2.2-writer" work before, just asking??

It worked under Dapper and Edgy, anyway. But not since I upgraded.

[QUOTE=steve.horsley]]I thiink that your problem is that "openoffice.org2.2-writer" is not the name of the executable but of the launcher description. The instructions below are for Ubuntu but there must be a very close equivalent in Kubuntu.

Right-click your menu and choose Edit Menus. Open the launcher for OpenOffice (a different launcher for each doc-type), select the Properties and change the Command to:
/opt/openoffice.org2.2/program/soffice -writer %U
This (I think) relies on leavinf fthe original OOo installed, and just modifies the launchers that the original OOo package installs.

P.S. the at the end, %U may well be a nautilus thing (it is only the executable path that I changed - the -writer %U was there before). You will have to use the K menu method of representing the filename of course.[/quote]

Thanks, Steve. I'll give it a go. Cheers.

---

