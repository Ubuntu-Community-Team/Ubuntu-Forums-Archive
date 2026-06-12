---
title: "Clean user profile?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by persofi on 2008-04-08
Hi,
I'd like to know if something like this is possible / easily implementable in Ubuntu:
I need to finish some ugly projecs that I'm hugely procrastinating on, for that I would like an Ubuntu User profile which has no internet access, just really basic programs as gedit,kyle etc... 
However I do not know how I set this up without messing up my main user account, for example If I deactivate my network connection in the 2nd profile, it is deactivated in the first also... And I dont want to have to change everything back all the time (or even reinstall programs).
Any help is appreciated, thx!

---

### Post by kostkon on 2008-04-08
Just create a new user that does not have permission to access the network, CD/DVD drive, etc.

Every permissions you set for this user will not affect your other (main) user account.

---

### Post by persofi on 2008-04-08
> **kostkon said:**
> Just create a new user that does not have permission to access the network, CD/DVD drive, etc.

Every permissions you set for this user will not affect your other (main) user account.

How do I do that? I created a new user and did not give click any of the checkboxes in user rights. However as I logged in under that name, I could access the internet no problem. Then I deactivated the network, and when I logged in under my main account, it was deactivated there as well.

---

### Post by bapoumba on 2008-04-08
[http://www.ubuntu-unleashed.com/2007/10/howto-disable-any-ubuntu-users-internet.html]("http://www.ubuntu-unleashed.com/2007/10/howto-disable-any-ubuntu-users-internet.html")
May be here ?

---

### Post by kostkon on 2008-04-08
You could also try to go to *System -> Administration -> Users and Groups*, select the *Properties* for a user and go to the *Priviledges* tab. There, you will be able to disable access to many resources of the system.

Another option would be to install *Pessulus*, the lockdown editor of *Gnome*, for a more fine-tuned access policy. Although, this solution may be a little too much.

---

### Post by kostkon on 2008-04-08
You could also try the [*LeechBlock*]("https://addons.mozilla.org/en-US/firefox/addon/4476") Firefox extension which is especially made for procrastinators. ;) [Here is a nice article]("http://lifehacker.com/374812/save-yourself-from-time-sinks-online-with-leechblock") about it.

---

