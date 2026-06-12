---
title: "Help! Newbie mistake with &quot;root&quot;"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by raysircher on 2007-03-11
I'm brand new with Ubuntu 6.10, and I've fouled it up already.  While setting up user accounts, I saw "root" in the list and thought that it was similar to Windows Administrator.  I changed the password for "root" and removed the system administration option from my first user account.  Now, the user account has no option for adding and removing programs, accessing users and groups, accessing terminal, etc. - and I don't know how to re-access "root" to change things back to how they should be.

Any help would be appreciated, and public apologies for my stupidity.

---

### Post by rjfioravanti on 2007-03-11
You can use the 'sudo' command to run commands with root privileges. So if you are trying to install a program, and your main login doesn't have the necessary privilieges, just say

```

sudo <command>

```

and you should be able to do whatever you are trying to do

---

### Post by Najand on 2007-03-11
> **raysircher said:**
> I'm brand new with Ubuntu 6.10, and I've fouled it up already.  While setting up user accounts, I saw "root" in the list and thought that it was similar to Windows Administrator.  I changed the password for "root" and removed the system administration option from my first user account.  Now, the user account has no option for adding and removing programs, accessing users and groups, accessing terminal, etc. - and I don't know how to re-access "root" to change things back to how they should be.

Any help would be appreciated, and public apologies for my stupidity.
Open a terminal;
Use "su" command in the terminal;
Enter your root password;
Use "gedit /etc/group" to edit your groups;
type your  username after "adm:x:4"
Save it.
Push Ctrl+Alt+BackSpace to restart X.
You would be able to use your account afterwards.

---

### Post by Najand on 2007-03-11
> **rjfioravanti said:**
> You can use the 'sudo' command to run commands with root privileges. So if you are trying to install a program, and your main login doesn't have the necessary privilieges, just say

```

sudo <command>

```

and you should be able to do whatever you are trying to do

He cannot do sudo when his user ID is not  in the group: "adm"!

---

### Post by raysircher on 2007-03-11
I think I followed your instructions, but it didn't solve the problem.

When I opened terminal, it had "first user name@computer name":  I entered "su", hit <enter>, and was prompted for the password.  I put in the root password, and got this message:  "To run a command as administrator (user "root), use "sudo" command".  Beneath that was a new line:  "root@computer name:/home/first user name#".  I put in "gedit /etc/group" and hit <enter>.  In the box that opened up, the first user name, "root", and second user name were already listed after "adm:x:4".  I restarted as you said, but nothing was changed with the first user account.

Have I done something serious enough that I would have to completely reinstall Ubuntu?

Thanks.

---

### Post by konst88 on 2007-03-11
Enter recovery mode.
Type:
adduser [user] adm
Where [user]=you user name, without [ ].

---

### Post by Najand on 2007-03-11
Ok, Then let us use another way. 
Use "su" to switch your user to "root" as I said above.
Now, use:
```

sudoedit /etc/sudoers

```
Add the following line under the line starting with "root"
```

<USERNAME>         ALL=(ALL)  ALL

```
Note to change <USERNAME> with your username.
Save it. And  restart your X.

---

### Post by raysircher on 2007-03-11
> **konst88 said:**
> Enter recovery mode.
Type:
adduser [user] adm
Where [user]=you user name, without [ ].

Tried that.  Message came up saying that the user name was already in the Adm group.  However, when I restart the program, no change.  The first user still doesn't have root privileges.

---

### Post by raysircher on 2007-03-11
> **Najand said:**
> Ok, Then let us use another way. 
Use "su" to switch your user to "root" as I said above.
Now, use:
```

sudoedit /etc/sudoers

```
Add the following line under the line starting with "root"
```

<USERNAME>         ALL=(ALL)  ALL

```
Note to change <USERNAME> with your username.
Save it. And  restart your X.

I tried this with no success.

---

