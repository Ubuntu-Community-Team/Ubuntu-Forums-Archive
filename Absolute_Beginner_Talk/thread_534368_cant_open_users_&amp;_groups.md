---
title: "cant open users &amp; groups?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2007-08-25
I updated Dapper to 2.6.17-12-386

when I click "users and groups" I get:

"the configuration could not be loaded - you are not allowed to access the system configuration"

At the moment I am the only user?

---

### Post by ddrichardson on 2007-08-25
Check out this [post]("http://ubuntuforums.org/showthread.php?t=532778").

---

### Post by kudos1uk on 2007-08-25
Thanks, I just tried that:

> **Ray190e said:**
> I fixed it :) here is how i did it 
1. open terminal and typed "su"
this asked me for a password , I entered my root password
2. then typed "gksudo user-admin" ,this gave me the the users and groups menu to fix me mess.

Thanks for the Help]

I did the first bit but it asked for a "root password" but when I put in my user password it says failed.

I could do part 2 though as that asked for my user password but I still can't set access to users and groups.

Sudo still works fine in terminal? I dont know what caused this I have not changed any setting just updated.





Edit: when I do id in terminal it says i'm a member of admin?

---

### Post by ddrichardson on 2007-08-25
When it fails, does it say "Authentication fail"?

---

### Post by kudos1uk on 2007-08-25
yes it does, I retyped it to be sure

I also can only mark apps for download later

---

### Post by ddrichardson on 2007-08-25
It looks as though you are no longer a member of the administrator group. Boot into a recovery console and check /etc/group.

Make sure that there is a line something like:```
admin:x:106:username
``` where username is your username.

---

### Post by kudos1uk on 2007-08-25
when I do "id" in terminal it says in in group 4 admin.

I can also use sudo, it asks my password and is accepted.

Its just when I type "su" it asks for a passwork and says "authentication failed sorry"

I have just had a callout so am going to have to run out the door, thanks for helping with this I will get back to it later.

Tony

---

### Post by kudos1uk on 2007-08-25
> **ddrichardson said:**
> It looks as though you are no longer a member of the administrator group. Boot into a recovery console and check /etc/group.

Make sure that there is a line something like:```
admin:x:106:username
``` where username is your username.


There are lots of entrys with my username, those with admin in them are:


lpadmin:x:106:username
admin:x:112:username

---

### Post by ddrichardson on 2007-08-25
OK you're in the admin group. Why are you using su rather than sudo?

---

### Post by kudos1uk on 2007-08-25
> **ddrichardson said:**
> OK you're in the admin group. Why are you using su rather than sudo?

The link to the thread you gave me earlier had this is it:

> I fixed it  here is how i did it 
1. open terminal and typed "su"
this asked me for a password , I entered my root password
2. then typed "gksudo user-admin" ,this gave me the the users and groups menu to fix me mess.

Thanks for the Help]

---

### Post by ddrichardson on 2007-08-25
Sorry I got confused, there are a couple of similar threads. Can you run```
gksudo user-admin
```

---

### Post by kudos1uk on 2007-08-26
Sorry for the delay, when I type that it asks for my password in a new popup window when I put it in the popup goes and terminal returns to a new command prompt I then clicked "user & groups" but got the same message as before:

> **The configuration could not be loaded **
you are not allowed to access the system configuration"


---

### Post by kudos1uk on 2007-08-26
This apperas to be a big issue, I found this:

[http://ubuntuforums.org/showthread.php?t=286260](http://ubuntuforums.org/showthread.php?t=286260)

And although I fixed it using this thread, upgrade still does not work.

---

### Post by jamvegan on 2007-08-26
> upgrade still does not work.

I don't see any other mention of an upgrade problem in this thread.  What issue are you encountering with upgrading?

---

### Post by kudos1uk on 2007-08-27
I was getting the message listed in this thread so did the Dbus reinstall which cured the problem.

When I checked upgrade it said there were none but 7.04 was available, due to the problems I though I would upgrade the agree screen came up which I said yes to then it sarted to install then stopped and the same old message appeared.

It the same message everyone was getting when they tried to click "users and groups"

> **The configuration could not be loaded**
You are not allowed to access the system configuration.

---

