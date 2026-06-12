---
title: "total noob, please help"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by walmartboi on 2008-03-16
okay so im a total noob,

i just installed ubuntu 7.10 server edition.

everything seems to have installed properly.

i have rebooted and logged into my box, 

i have tried to access root and so far have been unsuccesful 
in my attempts...

i have recorded all steps during my installation process, im not posting 
them at this point though.

every time i have attempted to log into root i have gotten these responses:

authentication failed
username is not in the sudoersfile. this incident will be reported

i have tried sudo, su, su -, sudo -s etc. none have worked.

at this point i have attempted everything i could find documentation online. i guess i dont really need to login as root at this point, i just need to know how to do and that it is possible.

"any help with this is greatly appreciated"

my goal for right now is to set something up locally for testing purposes.
i just want to have this server locally so i can upload any web related projects locally for testing purposes. any documentation or how-to's
are greatly appreciated.  anyone able to offer me any information on where to start my journey? i hope your out there and can help me out.

---

### Post by Belliinator on 2008-03-16
In Ubuntu, I don't think you can log in as root, you have to sudo every administrative task you do and type the password in as a normal user.

---

### Post by TeoBigusGeekus on 2008-03-16
Go to System->Administration->Login Window
Security tab and choose Allow local system administrator login

Before that, you have to go of course to 
System->Administration->Users and groups 
and set a password for root.

---

### Post by walmartboi on 2008-03-16
okay, i dont know if it is possible to log in as root...

as far as having to sudo every admin task, when i have tried to sudo
i keep have issues and have been username is not in the sudoersfile.

---

### Post by walmartboi on 2008-03-16
TeoBigusGeekus,

im running server not desktop and there are no tabs to click...

like i said im a noob but im not sure how to relate desktop solutions to server solutions.

---

### Post by mytips on 2008-03-16
Anyway you can change the root password and try again

---

### Post by walmartboi on 2008-03-16
during the install it never asked for a root passwd, i have found some steps for the desktop version of ubuntu on changing/working with root passwd etc. but not for the server edition

---

### Post by TeoBigusGeekus on 2008-03-16
I'm sorry mate, I've never worked with the server edition.
Are you sure you don't have a Login Window option under System->Administration?

---

### Post by walmartboi on 2008-03-16
i actually have no idea what kind of options i have working with this edition or how to access them, all the documentation i have found relates to the desktop edition.  i appreciate the response though.

---

### Post by mali2297 on 2008-03-16
> **walmartboi said:**
> during the install it never asked for a root passwd, i have found some steps for the desktop version of ubuntu on changing/working with root passwd etc. but not for the server edition

It should be the same as the password for the user that was created at installation.

---

### Post by jediscout on 2008-03-16
I would tend to think that it would be at least similar to the way desktop does it. It just might be placed somewhere else than where we think it is. Server edition could be a bit different. I have no clue to offer, I'm just getting comfortable with the desktop Ubuntu.

---

### Post by 3rdalbum on 2008-03-16
If you want a root terminal, log into your user account and type:

```
sudo su
```

Your prompt will change to reflect that you are in a root terminal.

To exit the terminal and go back to being a normal limited user, type:

```
exit
```

---

### Post by walmartboi on 2008-03-16
in response to 3rdalbum,

all sudo cmds are not working with the user account i created... 
responses like: authentication failed, user not in sudoers file etc.
i have tried several sudo/su cmds and none work

jediscout, there is no gui on the server edition. no point click... 
just cmds. 

in response to mali2297, 

i was under the assumption from the documentation that the root passwd would be the same as the user account passwd i created or i would at least be able to use that somehow to set the root passwd.

all attempts to set the root passwd have failed.

---

### Post by mali2297 on 2008-03-16
Can't you boot in *recovery mode*? 

That will log you in as root without asking for password (at least in the Desktop Edition).

---

### Post by walmartboi on 2008-03-16
okay so booting in recovery logged me in as root, thank you!

now i guess i need to adjust my sudoers file to include my user account info in it as well as set up my passwd for root.

anyone know any of these commands or where to find some info?

---

### Post by jken146 on 2008-03-16
The first user (created at install) should be a member of the admin group and therefore have sudo rights.  If this is not the case, go to recovery mode and type ```
useradd -G username admin
``` replacing *username* with the username of the user in question.

If you need to reset the password of that user, type ```
passwd username
```

You shouldn't need to edit /etc/sudoers and you certainly don't need to log in as root.

Some more info: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bsharp on 2008-03-16
*edit: What was said above is a better solution

---

### Post by walmartboi on 2008-03-16
alright, thank you everyone for all the help and input. I now know how to log in as root via recovery mode as well as enable and disable the root account via ubuntu documentation and i now have my user account running sudo cmds. all the input was a real help... thanks.

---

