---
title: "what is root password by default?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by larry wales on 2007-05-05
Hi all,

I just installed Fiesty and cannot seem to log into root.  Can anyone tell me what is the default password?  Or better yet, how I can go about checking this myself?

thank you,

-larry

---

### Post by tophatandy on 2007-05-05
its your password by default.

that is the first account you made.

---

### Post by Pobega on 2007-05-05
Ubuntu doesn't use a root account, it uses the sudo command to give the current user superuser access. This is for both security reasons, and to simplify things. If you want a root account you could always run the *passwd* command using sudo, and this will enable root logins.

---

### Post by rillip on 2007-05-05
Check out this site:

[http://www.nukesilo.com/2007/03/06/enabling-the-root-user-password-on-ubuntu/](http://www.nukesilo.com/2007/03/06/enabling-the-root-user-password-on-ubuntu/)

Tells you how to enable, test, with screen shots.

Usage of root is discouraged, naturally.  I believe by default the root user has no password set, (it is not blank, but is a representation of the empty string), thus making it impossible to login with.

---

### Post by taurus on 2007-05-05
Here's something for you to read.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tophatandy on 2007-05-05
there is a root acount..
you just access it to give you superuser privleges like you said..

but it is there by default...

---

### Post by larry wales on 2007-05-05
oh dear.  I tried using the password I created upon setting up, but it doesn't work.  I think the problem I'm having might be that I just deleted my keyring passwords:

[http://ubuntuforums.org/showthread.php?p=2442283](http://ubuntuforums.org/showthread.php?p=2442283)

I was trying to disable the Gnome key request that pops up every time I create a wireless connection.  In the instructions on the above link, the last step we perform is deleting our keyrings:

$ rm -fr ~/.gnome/keyrings/

Since I did this, the key request no longer appears, but I fear I may have inadvertently prevented myself from logging in as root.

Now, for example, when I'm prompted to enter the root password for things, my password no longer works.

Could anyone suggest how I might fix this?

-larry

---

