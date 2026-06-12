---
title: "Interesting user-admin problem"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-09-13
When other users is logged in on my PC with their own names, I am unable to add/change things to their accounts. It won't accept the password. I have to log them out and log in with my username. It then asks me my password and accepts it.

How can I change or add things for other users while logged in to their names then? 

Maybe there is a quicker way to add a new app shortcut to all users desktops? (Currently, I have to add it from under my username manually to their desktops.)

---

### Post by Muhammad on 2005-09-13
Do you know how to add more sudoers?

---

### Post by GrootBrak on 2005-09-13
[QUOTE=Muhammad]Do you know how to add more sudoers?[/QUOTE]

Yes. But that's not what I want to do. Why would I want more sudoers? One admin (me) should be enough for my family. Its only when I am in someone else's account, that I can't become temporary admin. The threads have enough of "sudo" things, why can't I become admin while using another account. As I explained, it won't accept the root password.

---

### Post by wmcbrine on 2005-09-13
Try su instead of sudo. (If necessary, you can su to your admin account, and then sudo.)

P.S. If you need GUI stuff, go to Applications, System Tools, New Login. You don't have to log out of the other user's session.

---

### Post by Nequeo on 2005-09-13
Have you heard of Sabayon?

[http://www.gnome.org/projects/sabayon/](http://www.gnome.org/projects/sabayon/)

It's going into Breezy, I believe... (Or Edubuntu at least) and may be closer to the 'C:\Documents and Settings\All Users\Desktop', of Windows XP fame.

Personally, I would just learn a scripting language! :) It might be easier than trying to get Sabayon to work, or messing around with security privaleges. Python is built right into Ubuntu, and is probably easier to learn than Bash. For example, the following code would create a program that copied its target files onto the Desktops of all users. 

```

#!/usr/bin/env python

import shutil, sys

### List your target users here ###
########################

users = ('brother', 'father', 'sister')

### Program code begins here ###
################################

targets = sys.argv[1:] 

for target in targets:
    for user in users:
        destination = '/home/%s/Desktop/' % user
        shutil.copy(target, destination)
        print 'Copied %s to %s' % (target, destination)
print 'Done!'

```

That's just an example, with no error checking... But it does work. If you wanted to use it, save it in /usr/bin, mark it as executable ( e.g. sudo chmod +x /usr/bin/copy_to_all) and then run it on the files you want to copy.

E.g.

```

cd Desktop
sudo copy_to_all New_Program.desktop Another_Program.desktop

```

---

