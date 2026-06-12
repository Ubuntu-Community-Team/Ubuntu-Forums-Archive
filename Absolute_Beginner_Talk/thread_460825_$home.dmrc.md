---
title: "$home/.dmrc"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by chinocracy on 2007-06-01
Hi, I decided to post anew since other solutions in other threads have not helped me.

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users.

I've tried the following:

```
sudo chown username:username /home/username/.dmrc

sudo chmod 755 chinocracy
```

and other such solutions, I'm still unable to log in. 

Happened when I made a new user account, Nochihee, and put it in the same group as chinocracy (admin user). I know I created another home folder, so I wonder why this happened. 

Can I delete the new account from the command line?

On Ubuntu/Kubuntu 6.06.

Thanks.

---

### Post by aysiu on 2007-06-01
Have you also tried this? ```
sudo chmod 644 /home/username/.dmrc
```

---

### Post by chinocracy on 2007-06-01
Ah yes, the 644 option doesn't work either. 644 is for the admin account right? So I wonder what else to try... aside from reinstalling. Thanks.

---

### Post by aysiu on 2007-06-01
644 is for *any* account's .dmrc file, not just the admin account's.

---

### Post by gary_emms on 2007-06-01
I had the same, don't know what caused it.
I fixed it by setting .dmrc to 644 (sudo chmod 644 /home/username/.dmrc), then setting the directory /home/username to 755 (sudo chmod 755 /home/username)

Hope that this helps.
Gaz

---

### Post by chinocracy on 2007-06-01
I'll have to retry the solutions, maybe I didn't get the order correct as Gary Emms did. Tell you later when I get to my box at home. Thanks.

---

### Post by mendingo84 on 2007-06-01
if you want to remove a user take a look here [http://www.howtoforge.com/linux_remove_users]("http://www.howtoforge.com/linux_remove_users"). That's the professional way to do it ;). Or you could use "deluser"

---

### Post by chinocracy on 2007-06-01
Another step I'm thinking is changing the group of another user. Though I'll try the above solution if all else fails. Thanks, Mendingo84.

---

### Post by chinocracy on 2007-06-01
Just tried again. Yep, the chmod and chown command doesn't work... I gave the Nochihee account 644 permissions, and it logged in successfully in Gnome, though without admin rights... My own account still doesn't work. I wonder how I can create a new user or group from the command line... it is getting frustrating. Thanks.

EDIT: Wait, I didn't follow follow Gaz's method to the letter I see. OK, again.

---

### Post by aysiu on 2007-06-01
You can create a new user from the command-line like this: ```
sudo adduser *nameofnewuser*
sudo adduser *nameofnewuser* admin
``` Then log in as the new user and Alt-F2 ```
gksudo users-admin
``` to add that new user to the appropriate groups (audio, etc.)

---

### Post by chinocracy on 2007-06-01
Thanks for this approach, Aysiu. Will try it later. I also have been trying the command line from the Failsafe terminal rather than from Alt-F2. Also, tried Gaz's order of commands, but didn't work for me. I successfully deleted my other account name, using 'deluser', but it didn't help. OK, will try this latest approach, thanks.

---

### Post by chinocracy on 2007-06-02
Aysiu, your creation of a new user approach was the solution. I'm finally able to use my account safely again. The error was caused by my resetting the home folder of my main account to /root when it should have been /home/username! Thanks a million. 
A little OT,  is it also possible to safely change the /home folder to one of the folders in the partitions in /media? Thanks.

---

