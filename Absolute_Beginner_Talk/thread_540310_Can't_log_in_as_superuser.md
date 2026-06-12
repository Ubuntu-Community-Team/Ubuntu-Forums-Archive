---
title: "Can't log in as superuser"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-09-01
I was experimenting with automatic log on in Administrative window & set my wife for automatic log on. Now I can't get back to where I can log on as superuser because everytime I boot up it automatically logs her in as user.

---

### Post by Vadi on 2007-09-01
If you're talking about being root always, that's a really bad idea...

Otherwise, check in Users & Groups if she has administrative privileges?

---

### Post by mcduck on 2007-09-01
Either turn off the automatic login, or just go to System/Quit and select Log Out to get back to login screen.

---

### Post by sailor2001 on 2007-09-01
system/admin/login window/security

---

### Post by garyed on 2007-09-01
> **mcduck said:**
> Either turn off the automatic login, or just go to System/Quit and select LogOut to get back to login screen.

Thanks, that did the trick.
I couldn't turn off the automatic login because she evidently didn't have priveliges to do so.
  System>Administration>Log in Window wasn't even an option until I logged backed in.

---

### Post by garyed on 2007-09-01
> **Vadi said:**
> If you're talking about being root always, that's a really bad idea...



I keep reading about that but I'm not sure how to log in without being root .
When I log in at boot up it asks for my user & password. 
After that I assume I'm automatically root.
I'm not sure how to change that.

---

### Post by -SpaZ on 2007-09-01
- If you are thinking about running as root, don't do it.
- If that's not what you're talking about, just log her out and it should show the login screen.

---

### Post by mcduck on 2007-09-01
> **garyed said:**
> I keep reading about that but I'm not sure how to log in without being root .
When I log in at boot up it asks for my user & password. 
After that I assume I'm automatically root.
I'm not sure how to change that.

If you haven't set the root password and enabled root login yourself it's impossible that you would be root.

The first account created during Ubuntu install is not root account, it's a normal user who has rights to temporarily become root by using "sudo". The actual root account is disabled by default.

---

### Post by garyed on 2007-09-01
I guess that my question is "How do I know if I'm running as root"

In system>administation>users& groups 
it shows 

Name          Login Name      Home Directory

myname      myname          /home/myname
root               root                  /root 
wifename   wifename        /home/wifename

---

### Post by -SpaZ on 2007-09-01
> **garyed said:**
> I guess that my question is "How do I know if I'm running as root"

In system>administation>users& groups 
it shows 

Name          Login Name      Home Directory

myname      myname          /home/myname
root               root                  /root 
wifename   wifename        /home/wifename

Believe me, you would know if you are running as root.  At the login screen you would have to log in as root, which is really not advisable.

---

### Post by mcduck on 2007-09-01
> **garyed said:**
> I guess that my question is "How do I know if I'm running as root"

Easy.Open a terminal and it will tell the name of the user you are currently. Of course you should now what user name you used when logging in even without checking it somewhere afterwards ..;)

---

### Post by garyed on 2007-09-01
Thanks everybody I finally got it.
I remember trying to learn DOS almost 20 years ago when I got my first computer.
There was no internet & very little help because very few people even had computers.
All I had was a DOS manual so I really appreciate all the help you guys are willing to provide.
I hope one day I'll be able to help someone else.

---

### Post by DM was on fire! on 2007-09-01
Nautilus will tell you, as well as terminal:

[[IMG]http://img265.imageshack.us/img265/7082/nautiluscomparelk2.th.png[/IMG]](http://img265.imageshack.us/my.php?image=nautiluscomparelk2.png) [[IMG]http://img410.imageshack.us/img410/3084/terminalbl5.th.png[/IMG]](http://img410.imageshack.us/my.php?image=terminalbl5.png)

(sorry they're so big)

Also, if you logged into root via the GDM, you'll have a different desktop or theme.
Instead of what wallpaper you have on your account (ie: dm@ubuntu, as opposed to root@ubuntu), you'll have the default Ubuntu desktop and Human theme.

---

