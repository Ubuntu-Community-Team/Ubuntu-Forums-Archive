---
title: "help cant login: No Profile for user 'myname' found"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by emrcookie on 2006-06-12
the erros is shown in ~/.xsession-errors as following:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mengy"/etc/gdm/Xsession: Beginning session setup...
No profile for user 'mengy' found

what can I do? thanks very much!!

---

### Post by catlett on 2006-06-12
What happens when you start your computer? Does it take you to the ubuntu login page? Is that where you get the error? Do you only get a text based login (kind of like a command prompt)
When do you get this error? How far do you get in the Ubuntu start up process before you recerive this error? Which install disk did you use?

---

### Post by emrcookie on 2006-06-12
Thanks. When I start my computer it take me to the login page. I could input my user name 'mengy' and passwd. After that the screen send me a windows tell me all that errors I posted. I hit ok the system go back to the login screen. I input myname and password it happen again. 

I got this error just now. When I restart my computer I can't login again. Yesterday I creat a ~/.profile in my $HOME add 'PATH=$PATH:$HOME' some thing like that. Now I delete it. 

I could use another linux system to login this computer to see all the file. I find the errors saved in ~/.xsession-errors. 

I install it in my master disk. I have another win system in slave disk.

I hope all these info is helpful. Thanks.

---

### Post by emrcookie on 2006-06-12
who could help me?

---

### Post by catlett on 2006-06-12
Sorry I didn't see your re-post. Can you boot with the Ubuntu recovery mode?
If you can do it. You will get a root login. From there you can add a user. I would add mengy. The command is ```
adduser
``` 
I never rtan this command and whern I searched the wiki it wasn't that helpfull. It said to run man adduser. Maybe you can maqke more out of it than me [https://wiki.ubuntu.com/AddUsersHowto?highlight=%28to%29%7C%28how%29%7C%28add%29%7C%28user%29](https://wiki.ubuntu.com/AddUsersHowto?highlight=%28to%29%7C%28how%29%7C%28add%29%7C%28user%29)

The solution is to choose Ubuntu recovery mode at the grub menu. When you get to the root command line. Enter the command to add a user. Then reboot and enter the system under that user. (hopefully you can use mengy like you wanted to)

Does anyone have familiarity with adding a user from the command line?

---

### Post by emrcookie on 2006-06-12
I think mengy is still exsist because I could remote to login my computer by use it. But some errors happen when I login it locally.

---

