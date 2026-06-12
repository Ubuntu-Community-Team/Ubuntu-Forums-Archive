---
title: "I have 700mb CDs. The ISO file is just over 700 MB?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by gwdevoar on 2006-08-27
I have 700mb CDs. The ISO file is just over 700 MB. Can I make the ISO file smaller by removing a file or two? Do I need all the files   or should I just buy larger CDs?

---

### Post by bodhi.zazen on 2006-08-27
go ahead and burn the iso. You should be fine.

---

### Post by gwdevoar on 2006-08-27
> **bodhi.zazen said:**
> go ahead and burn the iso. You should be fine.

Thanks for your reply. 
I tried to burn the cd, the Burner SW let me burn it but it did not work. The ISO file size is 713,550 kb per the file manager, the CDBurnerXP Pro SW shows I am 120.94 MB short on the CD.

---

### Post by bodhi.zazen on 2006-08-27
Tough break. In my experience some iso's that appear > 70 Mb on disk will fit on a 700 Mb CD. I do not understand why this is.

I would advise a DVD as I do not think the 800 Mb CD's are reliable (not to mention they are over priced).

Of course if yo do not have a DVD burner...

---

### Post by gwdevoar on 2006-08-27
Thanks for the help.

---

### Post by p.i.m.p on 2006-08-27
i dont know much about this but couldnt he try using overburn?

---

### Post by meborc on 2006-08-27
ahh, ran into the problem yesterday miself... i also thought about overburn... i know for a fact that gnomebaker supports overburn... but it was late and i just couldn't find the right place under the preferences where to put the tic to (i'm common gnome dumbuser :grin: ) so i just let it be...

i guess there should be a command with -overburn option... but man gnomebaker didn't give me anything... ahh... i try later with k3b under kubuntu... as it is said, kde programs are more sophisticated than gnomes... :-\"

---

### Post by dasunst3r on 2006-08-27
Remember to take into account that 700 MB = 700 * 1024^2 = 734,003,200 bytes.

---

### Post by steve.horsley on 2006-08-27
Also remember that the capacity of the CD is 700M oc contents (I think), wheras a .ISO file is an image of a CD and the CD flesystem, in the same way that 2M unformatted floppies could only hold 1.44M of data after the filesystem was added.

---

### Post by Bachstelze on 2006-08-27
Where did you get your ISO from ? Is the md5sum correct ?

---

### Post by gwdevoar on 2006-08-27
The 2 files I tried to burn are ubuntu-6.06.1-alternate-i386.iso 713,550 kb and ubuntu-6.06.1-desktop-i386.iso at 715,172 kb. I realize that would not include overhead on the CD. The SW I am using is CDBurnerXP pro 3. What is over burn? I will research it to see if that works.
Thanks

---

### Post by steve.horsley on 2006-08-27
Overburn is where you burn more than the CD is supposed ot hold. I think it's done by burning extra tracks outside the standard area.

You shouldn't need to overburn the installer CDs. But you must burn them **as an image**. This is differen to just burning the .iso file to the CD. Hopefully, there's an option to do that somewhere in that software.

---

### Post by gwdevoar on 2006-08-28
Thanks Steve

That worked on one file using the WindowsXP cd burning SW and the other file was somehow corrupted. I am going to download another copy.

Thanks to everyone for your help.

---

