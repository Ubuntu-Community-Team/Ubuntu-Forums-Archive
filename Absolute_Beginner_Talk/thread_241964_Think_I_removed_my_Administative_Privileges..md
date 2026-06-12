---
title: "Think I removed my Administative Privileges."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-08-23
I was messing around in Users and Groups and I think I unchecked the 'Administartive Privileges' option (under the Properties tab) because now when I go System>Administration> and select Users and Groups it seems to try to load for a few seconds and then just goes away (this is happening to most applications under System>Administration): any idea how I can get this back?
Thanks for your time.
(edit: Edited Title from "I think I removed my admin...")

---

### Post by deadgobby on 2006-08-23
Can you still log in as root? When you go into users/groups do you even get the promt for root password?

---

### Post by fiver22 on 2006-08-23
Yes it prompts me for the password -which I enter succesfully but then I get a pop-up saying "...you don't have the right to do that..."(That's essentially what it says -I can't get the exact words untill my password expires again)
Any ideas?
Thanks for your reply -I'll try to answer any questions I can about it.

> **deadgobby said:**
> Can you still log in as root? When you go into users/groups do you even get the promt for root password?

---

### Post by deadgobby on 2006-08-23
That is easy to change your root password and you be going in no time.
 Open up the terminal and type in 

sudo passwrd root

[http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

YOu should be able to change your root pass word.

Gobby

---

### Post by fiver22 on 2006-08-23
When I enter that command I get "You may not view or modify password information for root."
-Is it a password problem then? -Did I somehow change it?
I thought that maybe I had just disabled my ability to perform certain admin tasks... I'm afraid to log-out now -I might not be able to get back in.
Any other ideas I could try?
Thanks again for your time, I really appreciate it.
  

> **deadgobby said:**
> That is easy to change your root password and you be going in no time.
 Open up the terminal and type in 

sudo passwrd root

[http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

YOu should be able to change your root pass word.

Gobby

---

### Post by fiver22 on 2006-08-23
When I enter that command I get "You may not view or modify password information for root."
-Is it a password problem then? -Did I somehow change it?
I thought that maybe I had just disabled my ability to perform certain admin tasks... I'm afraid to log-out now -I might not be able to get back in.
Any other ideas I could try?
Thanks again for your time, I really appreciate it.
  

> **deadgobby said:**
> That is easy to change your root password and you be going in no time.
 Open up the terminal and type in 

sudo passwrd root

[http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

YOu should be able to change your root pass word.

Gobby

---

### Post by deadgobby on 2006-08-23
Hopefully you have not spent a lot of time installing Ubie. If worse comes to worse you may need to reinstall. I know if your use dail up that takes up time. Here is link for touble shooting.

 [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1412101](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1412101)

---

### Post by Thirsteh on 2006-08-23
You do not need to reinstall. If you're completely screwed, you can fix all this by entering Linux in single-user mode (emergency root login), and modify the user groups from there.

You may have to read up on single-user mode and command-line usergroup manipulation though, I'd throw some commands at you but I don't have Linux at the moment.

---

### Post by fiver22 on 2006-08-23
The exact pop-up I get when I enter my password is "Failed to run users-admin. The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."
-Does that mean my password is wrong? 
-Also the link you provided "[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1412101](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1412101)"  seems to link to the reply for this thread.
Thanks again for your responses.  

> **deadgobby said:**
> Hopefully you have not spent a lot of time installing Ubie. If worse comes to worse you may need to reinstall. I know if your use dail up that takes up time. Here is link for touble shooting.

 [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1412101](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1412101)

---

### Post by deadgobby on 2006-08-23
me bad
[https://help.ubuntu.com/community/SystemAdministration](https://help.ubuntu.com/community/SystemAdministration)

---

### Post by kwalo on 2006-08-23
> **Thirsteh said:**
> You do not need to reinstall. If you're completely screwed, you can fix all this by entering Linux in single-user mode (emergency root login), and modify the user groups from there.

You may have to read up on single-user mode and command-line usergroup manipulation though, I'd throw some commands at you but I don't have Linux at the moment.As **Thisteh** said: Enter recovery mode from group. You will be automatically logged in as root. Then type in the following command:```
nano /etc/group
``` This will start an editor. Find the line starting with admin (try pressing Ctrl-w and typeing 'admin'). Edit it to something like:```
admin:x:112:your_user_name
```Reboot your machine and that's it! You can run sudo again.

---

### Post by SeanHodges on 2006-08-23
As thirsteh said, reboot your computer and select the recovery mode on the boot screen (should be just below the default one)

When the computer has finished starting up, it should ask you for your root password. Type it in and you'll be at a root terminal.

One thing i can suggest is checking your permissions in /etc/sudoers...

your username should be in the file, with the settings 

```
ALL=(ALL) ALL
```

Let us know how you get on.

Cheers,

Sean

EDIT: Also check kwalo's suggestion, we posted at the same time :)

---

### Post by fiver22 on 2006-08-23
That did it -Thank you very much, 'kwalo'.
Also thanks to 'Thisteh', 'SeanHodges', and 'deadgobby' for their time as well.

> **kwalo said:**
> As **Thisteh** said: Enter recovery mode from group. You will be automatically logged in as root. Then type in the following command:```
nano /etc/group
``` This will start an editor. Find the line starting with admin (try pressing Ctrl-w and typeing 'admin'). Edit it to something like:```
admin:x:112:your_user_name
```Reboot your machine and that's it! You can run sudo again.

---

