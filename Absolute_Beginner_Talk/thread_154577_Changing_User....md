---
title: "Changing User..."
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by ZiGz on 2006-04-03
While I am not new to computers and know a few linux commands I am still a noob and would be embarrassed to post this anywhere else.

I have successfully installed Ubuntu, and I posting from the machine.  My problem is whenever I try to use any adminstrator type functions and get the "Changing User" box I can go no further.  I type in my user password it fails, I type in the root password and it fails also.  "Failed to run xxxx, Child terminated with 1 Status"

I know my root password works because I can use terminal and type "su" and I get in as root after typing my password.

What am I  missing?

Thanks

---

### Post by aysiu on 2006-04-03
I'm surprised you can *su* without enabling the root account.
Did you do an expert install? Sometimes that makes *sudo* not work properly.

---

### Post by ZiGz on 2006-04-03
Yes I did do an expert install as I wanted to be able to keep my WinxP partition. Is there something I can do?

---

### Post by aysiu on 2006-04-03
[QUOTE=ZiGz]Yes I did do an expert install as I wanted to be able to keep my WinxP partition. Is there something I can do?[/QUOTE] You don't need to do an expert install to keep your Windows XP partition. A regular install can do that. You should do a regular install.

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) will help you do a regular install and keep XP.

---

### Post by xenmax on 2006-04-03
You can add your current user account under sudoes list. This thread will help you do that
[http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)

aysiu, besides sudo problem (which can be fixed as indicated by thread), is there any other reason why you would recommend a regular install which would be a re-install rather than keeping current install.

Thanks.

---

### Post by aysiu on 2006-04-03
[QUOTE=xenmax]aysiu, besides sudo problem (which can be fixed as indicated by thread), is there any other reason why you would recommend a regular install which would be a re-install rather than keeping current install.[/QUOTE] No. It's basically that it doesn't take that long to install Ubuntu, and if you don't know what you're doing it's sometimes better to do a clean reinstall than try to "fix" things.

---

### Post by ZiGz on 2006-04-03
Followed those instructions in the Thread mentioned and everything is fine.  I will remember to avoid Expert mode in the future though.

Thanks both of you.

---

