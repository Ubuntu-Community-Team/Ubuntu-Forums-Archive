---
title: "[SOLVED] How do I delete a home directory?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by noobuntu7 on 2008-03-03
I need help... I'm *trying* to fix up this computer for a friend who doesn't have one, so I installed Xubuntu 7.10 on it. When I was going through the installation and it asked for a username and password I set them up as **Luke** (username) and ____ (password). That was for me, I was thinking that like Windows I could just set up the default account, then when I was ready to give it to him he could delete my user account and create his own. I now realize it's not apparently that simple, I can delete the user (Applications>System>Users and Groups). But it does not remove the home directory. I set up another account for my friend already (I am using that right now) and I gave him all permissions and privileges as system administrator. So I'm trying to delete my home directory (there are now two, mine and his) from *his* account.

I tried using
```
rm -r /home/luke
``` 
in the terminal, but it just says "Permission Denied". One time I got it to go past there and it says "dive into /home/luke? y/N" or something like that, if I answer with "y" then it says "dive into /home/luke/examples? y/N" and so on, for every single file. And every time I answer it goes on to the next file and says it could not dive into that file.

Anyway, I think I read something that said you can not delete a home directory with files in it. Is that true? Because /home/luke has a folder called **desktop** and one called **examples** and they both have files, but the desktop folder has an **x** on it and won't let me modify it or access it from  my friend's account.

Is there a simple way to delete that home directory? I would much appreciate any help. Thanks in advance!

---

### Post by zerhacke on 2008-03-03
sudo rm -rf /home/luke

---

### Post by philinux on 2008-03-03
You need 

sudo 

if front of the command

---

### Post by imT on 2008-03-03
```
sudo nautilus
```be careful thou what you do with admin privileges.

---

### Post by jeffus_il on 2008-03-03
And after that go to "Users and Groups" on the "System" menu and delete the user.

---

### Post by matherians2 on 2008-03-03
Here is a thought, why don't you reinstall Ubuntu and just create a user like sysadmin and simple a simple password.  Don't worry about deleting the home directory and just tell him the administrator password.  :)

---

### Post by jeffus_il on 2008-03-03
You can change the default account that is logged  onto by running ```
sudo gdmsetup
``` in a terminal.

---

### Post by Oldsoldier2003 on 2008-03-03
> **jeffus_il said:**
> You can change the default account that is logged  onto by running ```
sudo gdmsetup
``` in a terminal.
in the future you can do:
```
 deluser  --remove-home <user>
```
this removes the home directory and mailspool

or:

```
deluse --remove-all-files <user>
```

this cleans up alll files on the system owned by the user

---

### Post by Teber on 2008-03-03
> **matherians2 said:**
> Here is a thought, why don't you reinstall Ubuntu and just create a user like sysadmin and simple a simple password.  Don't worry about deleting the home directory and just tell him the administrator password.  :)

it's what i would have done. for good measure you may tell him to read this thread. much wisdom to be found here as is usual on this forum. :)

---

### Post by noobuntu7 on 2008-03-03
Thanks everyone!
using:
**sudo rm -r /home/luke** worked great! I just didn't have the sudo in front. And @matherians2 and Teber... Re-installing Xubuntu would have taken me about 5 hours (it's hard to install it on a 64MB RAM system) and the solution I used took me about 5 seconds. Thanks to everyone for helping though!

---

### Post by Teber on 2008-03-04
it's the ultimate result that counts innit? i'm happy to read that you fixed it the way you like best. now the fun begins for your friend, i should hope!

---

