---
title: "I can't change password or re-enable login password in Pinguy"
date: 2013-03-17
forum: Any Other OS
---

### Post by seanog on 2013-03-17
Hi,
I'm a linux  beginner. I recently installed Pinguy and am reasonably impressed so far, apart  from some small issues. First, I decided to disable the log in password  for faster logging on, but then I wanted to re-enable it in system  settings > user accounts > automatic login > off. But,  regardless of whether it is "on" or "off", I still log in automatically.  Any ideas? Also, I wanted to change my password, which I did in Terminal  > sudo passwd root > enter new unix password etc. And I get the  message: password updated successfully. But I find that my password  hasn't actually changed - the old one still works - the new one doesn't. Any help really  appreciated.

---

### Post by ajgreeny on 2013-03-17
You gave the root account a password and did not change your own when you used that command.
See RootSudo in my signature for more info on root accounts, etc, etc.

---

### Post by coffeecat on 2013-03-17
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by seanog on 2013-03-17
Thanks for the reply. I  had a look at that link, but unfortunately I'm none the wiser. Sorry, I don't understand what you mean: >  You gave the root account a password and did not change your own when you used that command. When I installed Pinguy, I was asked for a password for logging on. That's the only password I'm aware of, and it's the one which allowed me access to "change" it in Terminal, without success. And in system settings > user name, I see the auto login is "off", but in fact I am still logging in automatically.

---

