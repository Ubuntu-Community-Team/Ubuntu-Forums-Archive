---
title: "can't change password in phpMyAdmin"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by ljpm on 2006-10-23
Hi,

I am trying to install MythTV according to the howto.

In step 4 it says to configure MySQL.

> 4. Configure the database (MySQL) (1 minute)

MythTV uses MySQL extensively, so we have to get this set up before anything else. Fire up Firefox and in the address bar, type "localhost". Click the "phpmyadmin" directory. Type in "root" in the login form, and no password. Look down the resulting page for a "Change password" link, and click it; type in what you want your MySQL password to be. Note that this is *not* your root password, or your primary sudo account password. This one is separate, so make it whatever you want it to be. But remember it; we will need it later.

After the password is set, click the "Back" link (not the Back button in your browser). Click on the "Reload MySQL" link. Now, to verify that you password works, login again, using "root" as the user and your MySQL password that you just set; it should work. Logout from phpMyAdmin. Now try to log back in to phpMyAdmin using "root" and this time, no password. It should not let you in; done.

At this point, make sure you have logged out of phpMyAdmin.



I get to the point where it say to look down the resulting page for a change password link. 

I don't see a change password link.

please help.

---

### Post by SoggyCornflake on 2006-10-23
I think Ubuntu's package for mysql comes without the password set for root.  (Not for sure on that point.)

If you try **mysql -u root**, you may be able to get into mysql.  If you dare, you can select the mysql database and update the root password there.  (Be careful)


Another GUI you could use is  **mysql-admin** 
(You can use apt-get to install that.)  I think there's a way to changes passwords there. (Again I'm not sure and I'm also not at my ubuntu machine, so this is all from memory.)

---

### Post by salocinbake on 2006-10-23
Select privilege, the select the user you want to change password, and go to the RIGHT at the end.

There is a small person with a pencil. Click on it.

Voila.

Salo

---

