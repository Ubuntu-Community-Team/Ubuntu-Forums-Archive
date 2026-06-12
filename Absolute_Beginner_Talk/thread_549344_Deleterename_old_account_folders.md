---
title: "Delete/rename old account folders"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Baby Boy on 2007-09-12
When I deleted the two acounts I made, there was a message saying that their folders will not be deleted. That's true, they still are in my *home* folder, and the option *Move to Trash* is greyed out. 

I would also like to rename the account I am currently using, but when I rename it via *System->Administration->Users and Groups* the folder name remains the same. How do I get the permission to delete or rename these account folders?

Thank you in advance

---

### Post by macogw on 2007-09-12
sudo rm -rf /home/oldusername/ <-- delete the old users' stuff
sudo mv /home/youroldusername/ /home/yournewusername/ <-- move your stuff

---

### Post by Baby Boy on 2007-09-12
Thank you, macogw :).

---

### Post by digen on 2007-09-12
You can also use the script `userdel -r username` which will also remove the user's home directory. Useful instead of manually removing the directory.

---

