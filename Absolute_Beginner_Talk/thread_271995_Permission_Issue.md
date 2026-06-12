---
title: "Permission Issue?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2006-10-05
Hi all;

I am having an issue with file permission.  I have two users on a laptop; I’ve made a share folder under home: /home/share/.  So both users can read write to this folder.  Is there a way to make this folder’s permission so that: 
1) Doesn’t matter which user create the file into this share folder, the other user will be able to read write and execute the new file.
	
Because right now; if the 1st user create a file, in order for the 2nd user to have full control of the newly created file, the 1st user have to do chmod 775 <filename>

Thank you all in advance. 
Kpham.p

---

### Post by bulldog on 2006-10-05
You could see if you can change the rights for this map by right click the folder and go to properties-->tab rights and alter it to your likings.

---

### Post by kpham.p on 2006-10-05
thank you bulldog;

is there any command(s) that I can run in the terminal?  because a lot of time I can only ssh to this machine.  I'll try with the right click method if there's no easy way to do this by running terminal commands.

thank you so much.
kpham.p

---

### Post by bulldog on 2006-10-05
It's not really my cup of thea to do such things but you can try something with commands like "$ chmod $ chown $ chgrp $ file"  but you have to look it up.

---

### Post by kpham.p on 2006-10-05
cool thanks.

---

