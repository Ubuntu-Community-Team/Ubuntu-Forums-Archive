---
title: "hide folders in fiesty?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-05-05
how do i do this?
cheers

---

### Post by Tomosaur on 2007-05-05
Put a . before the name of the folder/file. Let's say you have a file 'myfile.txt'. Simply rename it to '.myfile.txt', and it will become hidden. Same thing for any file / folder.

---

### Post by Ptero-4 on 2007-05-05
rename them so that there´s a dot prefixing the folder´s name. That way it´s hidden.

---

### Post by keef247 on 2007-05-05
cheers guys worked real nice.nice one for speedy reply.thanks:)

---

### Post by troseph on 2007-05-25
What if it is a system folder such as LOST+FOUND?

---

### Post by Ek0nomik on 2007-05-25
> **troseph said:**
> What if it is a system folder such as LOST+FOUND?

Where is that folder?

---

### Post by lilro on 2007-05-25
i have that folder showing up in the folder above home

---

### Post by Ek0nomik on 2007-05-25
Well, you could rename to it .blahblah, but when somethings gets written there in the future, it will just go back to blahblah.  (notice the lack of a dot).  Generally files that are needed by the system you don't want to make hidden anyways.

---

### Post by ikonia on 2007-05-25
lost and found is a systems directory that stores data about lost data or data it can't associate with its correct place. Its used for recovering corruption.

eg: think of it as a .tmp file on a windows box.....sort of.

---

### Post by REDISISTone.nl on 2007-05-25
Just a Tip,

If you want to show your hidden folders and files, use ctr+h ;)

---

### Post by Najand on 2007-05-25
You should not remove or  rename LOST+FOUND folder (you can find it in every partitions highest directory). It is a system folder and renaming it might have serious damage to your system.

---

### Post by mcduck on 2007-05-25
You can hide any directory (without changing it's name) by creating a file called .hidden and typing names of files and directories you want to hide to that file, one per line.

For example, if you wish to hide /LOST+FOUND create a file /.hidden and put LOST+FOUND on the first line of that file.

This only works with Nautilus, so you'll still see those directories from a terminal.

---

### Post by Ek0nomik on 2007-05-25
> **mcduck said:**
> You can hide any directory (without changing it's name) by creating a file called .hidden and typing names of files and directories you want to hide to that file, one per line.

For example, if you wish to hide /LOST+FOUND create a file /.hidden and put LOST+FOUND on the first line of that file.

This only works with Nautilus, so you'll still see those directories from a terminal.

Awesome, I didn't know that.

---

### Post by troseph on 2007-05-27
I want to hide it... but I don't think I can hide lost+found... Its on the root of all the new partitions I made...

---

### Post by ikonia on 2007-05-29
re-read the thread and re-read what is explained about lost+found directory.

---

### Post by troseph on 2007-06-07
Oh! Awesome. Thanks I didn't notice. the .hidden file worked. Thank you!

---

### Post by aymhenry on 2008-03-19
Ubuntu 7.10 could not see a hidden folder on a data DVD which was created by my window xp system.
so it is hidden by windows attribut , and do not start with"." like hidden linux files/folders. ctrl+h did not work to show the folder. is it a bug. ?

---

