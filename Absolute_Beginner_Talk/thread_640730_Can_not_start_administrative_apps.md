---
title: "Can not start administrative apps"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by pfam144 on 2007-12-14
Hello, I am fairly new to using Linux and I installed Ubuntu Gusty 7.10  to try to get it to work in our corporate environment, which is all windows. By using the sadms app I was able to authenticate it to my active directory. I can now log in with domain accounts to linux however with those accounts I can no start some administrative apps (Synaptic Packet Manager, Users and Groups Software Sources, etc). Even logging in with my local account on the system they will not start. It will put up the 'Starting Administrative Application' and the cursor will be the circle as if it was working but I am never prompted for a password and it just fails to load. I can load users and groups using 'sudo users-admin' from the terminal. I do not know the commands to start others from the terminal but I am sure that they will work. Just for testing I enabled the root account to login to the gui and was able to run everything. I found on the forum that when people had this problem it was because of hostname issues but that is not the problem as far as I can tell. Has anybody seen this problem before or have any ideas that can help?

---

### Post by spiderbatdad on 2007-12-14
well you touched on what i was thinking when you addressed hostname. Have you seen this article by Dr. Small. He talks about "no passwd" for sudoers of non-admin accounts?[http://php.8ez.com/drsmall/blog/?p=157](http://php.8ez.com/drsmall/blog/?p=157)
Don't know if it will help, but here's to bumping your post one time.

---

### Post by pfam144 on 2007-12-14
Thanks for the suggestion. I have added the following line to the sudoers file and I am still getting the same results.

username ALL = NOPASSWD: ALL

Additionally I do not think it is the hostname because I can ping my hostname and I am not getting the error that other people were posting when using the sudo command.

---

### Post by spiderbatdad on 2007-12-14
how about:```
ALL hostname = NOPASSWD: ALL
```

where "hostname" is your actual hostname. totally nusure of what i'm suggesting here by the way, and is way out of keeping with Dr's article, but i believe the syntax is closer than what you posted

---

### Post by pfam144 on 2007-12-14
This is not the syntax that was described in the article that you linked to nor anywhere else that describes editing the sudoers file. I really do not want to mess with that file if you are not sure the syntax is correct.

---

### Post by spiderbatdad on 2007-12-14
well i certainly wouldn't script it the way we have used as an example here, but Dr's article states: username hostname = NOPASSWD: /path/of/sudo/command, path/of/next/sudo/command

this seems apropos though, taken from sudo visudo:# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL
 where you would simply uncomment the line: %sudo ALL=NOPASSWD: ALL

Honestly I'm anxious to keep your post going. I'm interested too.Hoping someone with expertise will chime in.

---

### Post by pfam144 on 2007-12-17
Ok, this looks like everything is working now. I tried the command you suggested and it worked great.

```
ALL hostname = NOPASSWD: ALL
```

When I logged in with the domain account I could not see any of the admin apps in the system menu that were not working before. So I had to go to edit the etc/group file and put my domain username after my linux user name wherever it was.

```
example:
root:x:4:joe,joedomain
adm:x:4:joe,joedomain
```

Thanks for all the help

---

### Post by StrangeBrew on 2008-02-05
I have the same problem as described, only I can't seen to fix it. I tried various entries in /etc/sudoers and /etc/group with no luck. I can however start anything from a terminal, but it always asks for a password. Are there any logs or tools that can help me troubleshoot this?

thanks

---

### Post by PabloCardoso on 2008-04-08
> **pfam144 said:**
> Ok, this looks like everything is working now. I tried the command you suggested and it worked great.

```
ALL hostname = NOPASSWD: ALL
```

When I logged in with the domain account I could not see any of the admin apps in the system menu that were not working before. So I had to go to edit the etc/group file and put my domain username after my linux user name wherever it was.

```
example:
root:x:4:joe,joedomain
adm:x:4:joe,joedomain
```

Thanks for all the help

Actually that code is a little bit insecure, since any user could get root privileges. I'd suggest adding the NOPASSWD option only to the admin group. I'm using Ubuntu 7.1 and the following line in my sudoers did the trick:

```
%admin ALL=NOPASSWD: ALL
```

Obviously, I've added my domain user to the local 'admin' group in order for this to work!

HTH

---

### Post by Hendrixski on 2008-04-08
So wait... you created a new account to log into the active directory... but did you give that account "sudoers" privileges... that is the ability to run administrative applications.  if not, log back into one that does have said capability, and give that user sudo privilege.  :-)

---

