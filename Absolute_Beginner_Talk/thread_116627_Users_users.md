---
title: "Users users"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-01-13
If I type users at the prompt I get;

user   user

does this mean there are two users on my system called user? And if so, how do I delete one of them?

Also, if I go to User-Admin via the desktop it asks me for the root password, if I type it in, it knocks me back saying the password is wrong. BUT, if I go to terminal and type SU, and then the same password, I get root access. Why?

thanks for the help.

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=My-dial-up]If I type users at the prompt I get;

user   user

does this mean there are two users on my system called user? And if so, how do I delete one of them?

Also, if I go to User-Admin via the desktop it asks me for the root password, if I type it in, it knocks me back saying the password is wrong. BUT, if I go to terminal and type SU, and then the same password, I get root access. Why?

thanks for the help.[/quote] 
No, it is introducing you, to yourself,,,, :p Just kidding.

When you are using the User-Admin program, you are running in a sudo enviroment. sudo is a tool access administrative rights, for non-root users. The fact that it wont accept the root password is on purpose. A security feature AFAIK. 

Anyway, if you type su, you are asking to be THE superuser, aka ROOT, which is the same as being root. So you need the root password.

Just use the User-Admin, and give YOUR password that you setup during install. That user has sudo rights.

Hope that helps, If I was not clear, let me know, maybe I NEED coffeeeeeeeeee.

---

