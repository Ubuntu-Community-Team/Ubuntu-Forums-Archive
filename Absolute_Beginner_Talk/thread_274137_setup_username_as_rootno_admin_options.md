---
title: "setup username as root?no admin options?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by fnordportland on 2006-10-09
ok so for my username i used root and ubuntu refused to let me log in as root at the main startup screen in the gui,so a friend setup another acount doing something in the shell,now i can og in but my new acount dosent have admin privilges,thing like user/acount setting under the admin menu how do i change users privilges under a shell?sorry completly new to all this

---

### Post by GrimJa on 2006-10-09
Well under user management (sry, cant give you exact navigation right now, perhaps someone else can), you can see to it that YOUR account has administrative privaleges. 
You can add it to the root group.

But as for loggin in with root, all you have to do is enable the root account to log in with the GUI.
 I think its in the same section:-| 

-forgive me... I'm in windoze now.

---

### Post by MiXor on 2006-10-09
Hi there
For more information I suggest that you read aysiu's answer in the following thread : [http://ubuntuforums.org/showthread.php?t=268318&highlight=login+as+root](http://ubuntuforums.org/showthread.php?t=268318&highlight=login+as+root)
:KS

---

### Post by kerry_s on 2006-10-09
Just For future reference, for security the root account is disabled. The first user created gets admin rights and uses it by means of sudo.
Example open the filemanager as root:
sudo gedit

---

