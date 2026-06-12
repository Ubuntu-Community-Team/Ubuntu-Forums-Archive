---
title: "Wired &quot;Ubuntu&quot; User problem..."
date: 2009-08-28
forum: Apple Hardware Users
---

### Post by GuillermoZS on 2009-08-28
Hi!

I´m new to Ubuntu. I have a MacBook (aluminium) 5,1 and installed the **pre-made .iso** I downloaded from the installation instructions. During installation, I choosed Spanish as my language, and also chose a user name and a password.

After reboot, ubuntu was in English and I noticed I was logged in with a user called "Ubuntu" (not the name I introduced during installation), also the admin password is not the one I entered (I can not have admin privileges).

I tried to switch to the user I was supposed to have created but nothing (it does not exist)....

What can I do??

I guess it is something related to the pre-made.iso since when I rebooted and the "Ubuntu" user appeared there was a custom background image...

Thanks a lot!

---

### Post by amd-64 on 2009-08-29
It is easy to get admin privileges. On the start menu in grub, select recovery mode. 
This should get you to a text terminal where you can login without a password. 

Type passwd and select a new root password. 
Type exit or reboot to get to a graphics interface.

Once you have this, you may create users and passwords from the gnome menu System > administration > users and groups.

---

### Post by GuillermoZS on 2009-08-29
Hi! Thanks for the reply.

I changed the root password but when I go back to the graphic interface >Admin> Users and Groups this is what I see:

[IMG]http://img.photobucket.com/albums/v219/GuillermoZS/Screenshot-UsersSettings.png[/IMG]

I can not add a new user, if I press Unlock, the root password I chose doesn't work either....

How can I use the root pswd to change this?

Thanks a lot!!

---

### Post by GuillermoZS on 2009-08-29
Finally, I found out how to do it. In case anyone has the same problem:

- Boot in recovery mode.
- Type:
> passwd *username*
where *username* is the name of the user you want to change the password. In my case:
"passwd ubuntu" (if at first it&#347; not working, try Capitals for the first letter of the username).
- Reboot again and the password of the user should be changed. Now you have acces to the Users panel.

---

