---
title: "[SOLVED] User Switcher bug in Gutsy"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-11-20
The user switcher app in Gutsy has a bug, I think.

I have 3 users on the machine. I log into one of them and then use the user switcher app to login as another user. This part works fine. But when I finish with what I wanted to do and try to log out, I get a White Screen of Death. I have to hard reset to get out of it.

The log out works normally when I have logged in only as one user.

It seems that log out works only when there is one and only one user logged in.

Does anyone else have this problem? Any solutions?

---

### Post by jken146 on 2007-11-20
I have this problem intermittently.  I found that sometimes I can type in the password of the last user logged on (before the user who just logged out or switched out) and, although I can't see anything, I get back in.

---

### Post by master_kernel on 2007-11-20
This happened to me when I was using a compositor (xgl, sometimes aiglx) with compiz/beryl.

---

### Post by illbashu on 2007-11-20
this happens to me too... :(

---

### Post by louieb on 2007-11-20
Rather that use the user switching agent. I use Ctrl+Alt+F7 (or F8 [2nd user] ...)  Works in Dapper and Gutsy - was broke in Feisty.  Never used Edgy so don't know. 

Still have to use switch user to login the 1st time but after that the function keys work. 

To see which user is logged on to what terminal run the **finger **command.

Don't know if this will do anything for your logout problem but I haven't had that problem yet.

---

### Post by Inxsible on 2007-11-20
I think the bug is more related to having more than 1 user logged in at the same time.

This time I didn't use the User switching app. Just the regular Switch User from clicking the Red button. although, I think they both do the same thing.

The last thing to test would be if log out works when only one user is logged in.

Be right back :)

---

### Post by Inxsible on 2007-11-21
If only one user is logged in, then the logout works just fine !

I have determined, that if you switch users and then try to log out anyone of them, it produces a White Screen of Death. No matter how you switch users, either using the User switcher applet or the 'Switch User' under all the shutdown options.

This used to work in Feisty. Is there a solution to this problem?

---

### Post by kefurd06 on 2007-11-21
i get this exact same error. turn on machine, log in, switch user, enter username/password and log in, then log out, poof, white screen. i can then type the last account's password followed by the enter key to get back to my first account.

---

### Post by Inxsible on 2007-11-21
> **kefurd06 said:**
> i get this exact same error. turn on machine, log in, switch user, enter username/password and log in, then log out, poof, white screen. i can then type the last account's password followed by the enter key to get back to my first account.So do you do that in blind?

or can you see your password being typed on the screen ( i mean the black dots)

---

### Post by thierry34 on 2007-11-25
> **kefurd06 said:**
> i get this exact same error. turn on machine, log in, switch user, enter username/password and log in, then log out, poof, white screen. i can then type the last account's password followed by the enter key to get back to my first account.

Hi all,

It's the same for me. I'm able to type the password in the blind when I get to the white screen while switching user.

I found a workaround for not getting this white screen. Right click on the "User Switcher" applet and select "Preferences". then uncheck the "Lock the screen after switching users" option.

Not so secure but no more WSOD :-)

Thierry

---

### Post by chrisccoulson on 2007-11-25
> **thierry34 said:**
> Hi all,

It's the same for me. I'm able to type the password in the blind when I get to the white screen while switching user.

I found a workaround for not getting this white screen. Right click on the "User Switcher" applet and select "Preferences". then uncheck the "Lock the screen after switching users" option.

Not so secure but no more WSOD :-)

Thierry

That works for me also. I've seen other posts on the forum with the same workaround. Is there a bug report for this?

---

### Post by Inxsible on 2007-11-26
Sweet !!

I shall try it out tonight !

---

### Post by Inxsible on 2007-11-27
Yup that works !!

Thanks ! :D

---

