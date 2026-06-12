---
title: "Need Help , Desperate"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by bobrath on 2006-07-21
I did something stupid. I had an administrator account and folishly changed my home directory to /root.
Now I can't login , I have another account but it's a default account and can't do any administration tasks. How do I change my home directory back to /home/myname.. ? PLEASE , I need some help.
Thanks , desperate... Gasp

---

### Post by 5-HT on 2006-07-21
Easiest way would be to boot into recovery mode (press 'Esc' at the GRUB menu and select the relevant option) and edit the user's home directory in /etc/passwd appropriately.

Alternatively, as root in recovery mode, you could give the working user account sudo rights* and change the other user's home directory via the *Users and Groups* GUI using the functional account.


*One way of doing this is described in the following wiki page:[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).
There are other ways of granting a user sudo rights documented in various threads around the forums.

Hope that helps.

---

### Post by -deadcats on 2006-07-21
System>Administration>Users and Groups.

Click on Users, find your account, click on Properties, click on Advanced, change the home directory to /home/yourusername

regards,
-dc

---

### Post by Skia_42 on 2006-07-21
You remeber how you changed your home Directory to root correct? You can use the command control+option+f2 command to get access to the terminal, log in adn then you can use the > sudo -s command to gain root privledges for that session. Then you can change your home directory back to what it was. (Would you mind posting how you changed your home directory?

---

### Post by bobrath on 2006-07-21
@ deadcats.. Can't do that can I ? I'll need a terminal method. 
@5-HT what do I do in the /etc/passwd directory. Could need a little detail please.

---

### Post by bobrath on 2006-07-21
Went to Users and Groups in the Adminisrtation sub menu and changed my home directory. Not advisable though.

---

### Post by 5-HT on 2006-07-21
> **bobrath said:**
> 
@5-HT what do I do in the /etc/passwd directory. Could need a little detail please.

You should see a line in /etc/passwd pertaining to the user you would like to change the home directory of. It will start with the username of that account. To edit the home directory, the relevant text will be just before the user's default shell which is the last field on line.

For you, the end of that line may look like this:
```
:/root:/bin/bash 
``` 
You'll want to change it to:
```
:/home/<username>:/bin/bash 
``` (replacing <username> with the username of that account.)

As to the other suggestions in this thread, my understanding from your original post is that the working user account does not have sudo rights. If that is true, you will need to use the recovery mode to obtain root privileges.

Hope that helps, post again if you are still having problems.

---

