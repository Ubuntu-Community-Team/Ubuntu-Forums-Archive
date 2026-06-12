---
title: "oh!  I am not able to enter as root user!"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by DThurman on 2006-07-17
I just completed installing ubuntu and I discovered that I can log in as a normal user (since it asked for my username and password) but I am unable to log in as root user!

Is there a default password or something?

Thanks!
Dan

---

### Post by ewl1217 on 2006-07-17
Ubuntu uses sudo rather than using a root account. You can run a terminal-based program in as the root user, from your account, by typing in the terminal ```
sudo command
``` and run graphical applications with ```
gksudo command
```

(Just replace "command" with whatever you want to run)


For more information on this see [this page]("https://help.ubuntu.com/community/RootSudo").

You can also enable root by typing, at the terminal ```
sudo passwd
``` to set the root password.

---

### Post by jd65pl on 2006-07-17
Log in as user.Go to:
SYSTEM > ADMIN > LOGIN WINDOW > SECURITY > ALLOW SYSTEM ADMIN LOGIN

Change root password:
SYSTEM > ADMIN > USERS AND GROUPS
Check "show all"
Change root password.

**HOWEVER YOU CAN DO MOST THINGS IN UBUNTU IN TERMINAL USING "SUDO" BEFORE A COMMAND, LOGING IN AS ROOT CAN COMPROMISE SECURITY AND ISN'T SO ADVISED.**

thanks

---

### Post by reacocard on 2006-07-17
ubuntu disables root login by default. instead, put sudo before the command you wish to run as root, and enter your password. voila, root access! more info on sudo can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PriceChild on 2006-07-17
to get to a root terminal.... means you don't have to enable a root password most of the time... just use

sudo su

---

### Post by DThurman on 2006-07-17
Thanks to all that responded!

I am able to add swap space so I am a happy camper so far!

Now... time to update - sigh...  fun ](*,)

---

