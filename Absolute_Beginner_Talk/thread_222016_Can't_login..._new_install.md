---
title: "Can't login... new install"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2006-07-24
Hi,
I installed ubuntu 6.06 last night.
I loged in as OEM user, and then did "sudo oem-config-prepare"
as instructed.
Now I cannot login as the user I created for some reason, or as OEM user, not even as admin/root.
Anyone here can help me login and reset the login user?

---

### Post by taurus on 2006-07-24
From the GRUB menu, boot into recovery mode and change the password for your user, assuming as john, with

```

passwd john

```
Remember, upper case is not the same as lower case in Unix!!!

---

### Post by ROUBOS on 2006-07-24
when I try it, I get unknown user

is there a command to see the created users? delete them and create some?

---

### Post by jd65pl on 2006-07-24
Use 
```
ls /home
```
to see all user names

---

### Post by ROUBOS on 2006-07-24
/home/ has no users in there. nothing listed

So I guess my user was not created with the sudo oem-config-prepare command.

So how do I create one now? And why does it not login when I enter root as username and the password I inserted during the install?

---

### Post by jd65pl on 2006-07-24
root login is not enabled in the gui, not sure about command line

---

### Post by jd65pl on 2006-07-24
Try this to add an new user im not sure it will work tho

```

cd /home
ls <-- to view current accounts
mkdir *User Name* <--creates a new user
ls <-- view users again

```

---

### Post by Thund3rstruck on 2006-07-24
To login as root via command line execute

$sudo -s

Then create a user, add him to the sudoers group and you off

---

### Post by ROUBOS on 2006-07-24
add them to the sudoers group? how?
sorry noob here...

if I just create a user dir, how does it set it's password?
Will it just let me login with the admin password I setup during install???

EDIT >> Just created a dir, and exited. Gone back to the login gui screen, and it does nto log me in. :(

---

### Post by SilverBear on 2006-07-25
> I installed ubuntu 6.06 last night.
I loged in as OEM user, and then did "sudo oem-config-prepare"
as instructed.
Now I cannot login as the user I created for some reason, or as OEM user, not even as admin/root.
Anyone here can help me login and reset the login user?

Where did you read the instructions to do this kind of OEM login on a new install?  Can you give me a URL?

---

### Post by ROUBOS on 2006-07-25
Those instructions poped up on the screen after the installation.
Did not get them from a site.
Now I can't login at all. Need to create a user in safe mode, but I don't know how.
I created a directory in /home/ but it does not work.

---

### Post by justicerulesok on 2006-07-25
I would wipe & start again.  I only installed it last week for the first time.  It asked me for a username & password with me doing anything comnplicated.

On a basic install only the first user registered can use the sudo command & I would be worried that any new user you created now would not be able to sudo.

As you havn't made too many changes to the system I would think this 'cut your losses' approach would be the quickest & easyiest.  Sorry :-(

Justice.

---

### Post by ROUBOS on 2006-07-25
yes, it asked me for a username and password, and i don't know why it does not accept it or why it did not create it.
So I guess I should re-install it and see how I go.

Thanks for the replies everyone.

---

### Post by mcduck on 2006-07-25
This time forget about the OEM install and just do the normal install. OEM install only makes thinks more complicated but provides no advantage for home users. You only need it if you want to sell Computers with Ubuntu preinstalled..

---

### Post by sebz2005 on 2006-07-25
Go to the terminal and type:
```
sudo adduser (Name here)
```
Replace (Name here) with the username of your choice.
Type the password in, and continue to press enter untill i comes up saying:
```
Is this information correct? [Y/n]
```
Type **y** , restart the pc and you _should_ be able to login.

---

### Post by ROUBOS on 2006-07-25
Will this create a user able to sudo???

---

### Post by sebz2005 on 2006-07-25
No, but each time you want to do someing as root, just type

sudo -s

and insert the password and you'll be able to do anything as root.

---

### Post by ROUBOS on 2006-07-25
cool thanks :)

---

### Post by sebz2005 on 2006-07-25
So I'm guessing it worked?

---

### Post by ROUBOS on 2006-07-25
Yes it worked.
Yhanks:D

---

### Post by arkangel on 2006-07-25
#sudo -s users-admin
and play around

also  you may read  here 
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

---

### Post by taurus on 2006-07-25
Boot into recovery mode, then at the prompt, do

```

adduser -m -G adm,admin,video,audio,cdrom -s /bin/bash john
passwd john

```

---

### Post by ROUBOS on 2006-07-25
here we go. another issue. left the pc running to make coffee, I get back and it's frozen on the screensaver. Must be a 3d screensaver and it froze :(
Need to look up and fix the 3d card issues...

---

### Post by sebz2005 on 2006-07-25
What card is it?

---

### Post by 0okami on 2006-08-07
> **taurus said:**
> Boot into recovery mode, then at the prompt, do

```

adduser -m -G adm,admin,video,audio,cdrom -s /bin/bash john
passwd john

```

What exactly does this do? Im having issues with oem-config-prepare (i even tried twice because i thought i got it wrong the first time.

No users are listed in /home

same as previous user, i cant log in. 
I tried: sudo adduser

...but the system says "adduser: Only one or two names allowed." 

So im willing to try the above mentioned command, but I'd like to know what exactly it does before jumping at it.

bah... desperation kicked in and i tried it anyway. i got: 

Option g is ambiguous (gecos, gid, group)
Option s is ambiguous (shell, system)
adduser: only one or two names allowed. 

*extreamlly puzzled.*

---

### Post by 0okami on 2006-08-07
problem solved for me: It was the user name i had selected. It appears you have to use lower case characters and only alpha, not numeric. I was putting 0okami (zero) 

so by changing 0okami to ookami it now works fine. I re-ran "sudo oem-configure-prepare" from the recovery option and corrected the issue. 

Maybe this will help anyone else having this issue :)

---

