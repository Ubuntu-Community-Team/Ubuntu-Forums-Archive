---
title: "dual boot permission problem"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-02-24
I have a dual boot with Windows 2003 . On Windows I have two partitions which I have mounted successfully. While I can do anything as root , my user doesn’t have the permission to write to hda5 (the D partition on Windows) . I tried
 ```
sudo –S chmod 0757 /media/hda5
``` and it prompted me for a password , I put in my root password and it just said  try again (but the password is correct for sure) . I never have any problem with root password except for this command. I then switched to root  (using the same password the terminal refused to accept one line above) and ran the same command but the permissions didn’t change. 
I tried the’ Xfce fstab mount manager’ , there is an option there to change permission . It prompted me for the root password and again refused to accept the one I typed.  
What can I do then?

---

### Post by jimrz on 2006-02-24
what file system have you got on hda5?

---

### Post by aysiu on 2006-02-24
You can't chmod or chown a Windows partition.

See the fourth link of my signature.

---

### Post by seshomaru samma on 2006-02-25
[QUOTE=aysiu]You can't chmod or chown a Windows partition.

See the fourth link of my signature.[/QUOTE]

Thanks for the link ,yet:
i followed your instructions but the permissions now are still such that only root can write to it , i want my user to be able to as well..
another thing is that i couldnt use sudo at all , every command with sudo prompt me for a password which the terminal didnt accept ,its only when i switched to root (with the same password) that i could carry out those commands...
very strange....

---

### Post by seshomaru samma on 2006-02-25
[QUOTE=jimrz]what file system have you got on hda5?[/QUOTE]

FAT32   
:-D

---

### Post by aysiu on 2006-02-25
[QUOTE=seshomaru samma]Thanks for the link ,yet:
i followed your instructions but the permissions now are still such that only root can write to it , i want my user to be able to as well..[/quote] Is your Windows partition NTFS? If so, it's read-only--that's the way it is. FAT32 can be made to be read/write.

> another thing is that i couldnt use sudo at all , every command with sudo prompt me for a password which the terminal didnt accept ,its only when i switched to root (with the same password) that i could carry out those commands...
very strange.... Did you do an expert install? There should be no root account and root password.

---

### Post by PrivatePickle on 2006-02-25
> another thing is that i couldnt use sudo at all , every command with sudo prompt me for a password which the terminal didnt accept ,its only when i switched to root (with the same password) that i could carry out those commands...
very strange....

When using "sudo" your password is your user password that you log into ubuntu with not the root password.

---

### Post by PrivatePickle on 2006-02-25
They following link to chapter 5 of the starter guide should show you what you need.

[HTML]http://help.ubuntu.com/starterguide/C/ch05.html[/HTML]

---

### Post by seshomaru samma on 2006-02-25
thank you
problem solved!

---

