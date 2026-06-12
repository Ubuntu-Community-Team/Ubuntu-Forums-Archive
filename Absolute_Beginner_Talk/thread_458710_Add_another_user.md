---
title: "Add another user"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-29
I want to add a third user to this system root being 1 of them.  I have defined the 3rd user but if I logon at bootup I get a message - The administrator has disabled the system temporarily.  I want to add the third user so that I can sign on and anyone looking over my shoulder and noting password won't be able to use the password with the sudo command.

---

### Post by sankarv on 2007-05-29
check the system preferences settings for users and groups. that might help....

---

### Post by ICUR2Ys on 2007-05-30
I was unable to bring up the preferences for any part of users and groups.  Properties was no help.  Thank you for the suggestion.  I wish it had worked.

---

### Post by wormser on 2007-05-30
Check to see is you can switch to that user in the shell.  

```
su username
```

If that does not work try changing the password.

Another place to look is in /etc/passwd.  Look for that user and see if there is an :x:.  That x is the password which has been shadowed.  

```
less /etc/passwd
```

To make that command easier pipe it into grep.

```
less /etc/passwd | grep username
```

Good luck

---

### Post by ICUR2Ys on 2007-05-30
Well I don't know.

I did change to the other user.  Which was interesting because I discovered that I had not created its own unique home.  When I entered the second command the output didn't show either user.  I didn't notice if root was listed.

The third didn't cause grep to come up.  If I keyed in grep I was told to use the --help.

Thanks for the input.

---

### Post by ICUR2Ys on 2007-05-30
I think I made a mistake on entering the commands.  The output of the 3rd command is:

dace:x:1001:1000:icu,,,,:/home/dace:/bin/bash

It shows the 2 user ids.

It doesn't tell me any more than that.

---

### Post by wormser on 2007-05-30
> **ICUR2Ys said:**
> Well I don't know.

I did change to the other user.  Which was interesting because I discovered that I had not created its own unique home.  When I entered the second command the output didn't show either user.  I didn't notice if root was listed.

The third didn't cause grep to come up.  If I keyed in grep I was told to use the --help.

Thanks for the input.

Something went wrong when creating the user if there was not /home/username.

> **ICUR2Ys said:**
> I think I made a mistake on entering the commands.  The output of the 3rd command is:

dace:x:1001:1000:icu,,,,:/home/dace:/bin/bash

It shows the 2 user ids.

It doesn't tell me any more than that.

That out put is fine.  Dace should be your user name and the :x: is there for the password.  How did you create the account?  If you have no /home/ folder then there is no place to log into.  Try deleting the account and create it again.

---

### Post by ICUR2Ys on 2007-05-30
Well things are getting better.  I deleted the user and recreated it.  This time it had its /home/dace which seems right.  I rebooted, and tried to log in this time I received the message invalid user or password.  So I logged in normally and looked in Users and Groups.  

I am skipping a step After logging in normally the system came up and a message was displayed about and an invalid folder involving the new user.  I don't really remember the exact file name.

Then looking in Users and groups the user was removed.  So I will try to recreate it again.

---

### Post by wormser on 2007-05-30
Are you using a unique user name?  You only can have one user per name?  Your earlier post where you stated it showed up twice had me thinking about that.  How are you adding the user?  Are you using the **sudo adduser username**?

---

### Post by ICUR2Ys on 2007-05-30
I recreated the new user with the same name.  Then reentered Users and Groups and it was gone again.

So I created a new user with a different name. Then reentered Users and Groups and it was still there.

So now I will reboot and see if I can log in at bootup.

---

### Post by ICUR2Ys on 2007-05-30
It didn't work.  I am back to the original message at bootup.  I am going to give up for now and go to bed.  I will work on this again tomorrow.

Thank you very much for the help.  I am better off because now the /home is associated with the new user too.

I appreciate the help.

---

### Post by ICUR2Ys on 2007-06-01
I have the new user working now.  Thank you very much for the help.

---

