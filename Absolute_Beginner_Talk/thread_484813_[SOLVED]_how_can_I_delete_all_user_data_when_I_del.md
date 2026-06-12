---
title: "[SOLVED] how can I delete all user data when I delete the user account?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-26
I created a new user account to try something out. I went to System/Administration/Users and Groups.

Now, however, I would like to completely undo everything that "Add User" accomplished. I went back to "User and Groups", clicked the user account, and clicked "Delete". Then I got the following message:

 > This will disable this user's access to the system without deleting the user's home directory.

How do I delete the user's home directory, as well as with everything else that was created?

Thank you.

---

### Post by wieman01 on 2007-06-26
This way:
> sudo rm -r /home/*[COLOR="Red"]<user_name>[/COLOR]*

---

### Post by hanzj on 2007-06-26
Thanks. 
Some questions:
1) Is that the only thing that I would need to delete in order to complete undo what "Add User" did?
2) Is there no GUI/Point and Click/Newbie way of doing things?

---

### Post by wieman01 on 2007-06-26
Those would be all data that you need to remove. This is the whole point of Unix' user management.

As for the GUI, I am not sure if there is one available. You could you Nautilus of course, isn't there a root function for it?

Yes, in my experience there is a occasional need for command line, but usually it is much faster that way. Trying to configure Bluetooth which is a real command line nightmare if you ask me.

---

