---
title: "User no longer able to login"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-09-21
I can no longer login to a user account. (I can log into the sudo acct.)  The user account did work but now this message appears after the username/password entry: "*The system administrator has disabled your account.*" I do not remember disabling this account.

Interestingly, in this home LAN environment, I can access the user's file from an XP box.  I can also access them as SUDO.

How can I re-enable this user acct?

---

### Post by Pumalite on 2007-09-21
[http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)

[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

[http://sayspy.blogspot.com/2006/08/ignorant-newbie-adding-new-user-under.html](http://sayspy.blogspot.com/2006/08/ignorant-newbie-adding-new-user-under.html)

[http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html](http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html)

---

### Post by Ian-on-the-Trent on 2007-09-21
I've actually looked hard for this issue.  A Google search using the error message yielded few hits and most of those were not in a language I understand.  So I'm back at square 1.  But I will have a look at the links your provided.

---

### Post by Pumalite on 2007-09-21
You will come out enlightened.

---

### Post by Ian-on-the-Trent on 2007-09-24
The solution...I think.

I clicked through System>Adminsitration>User and Groups>User Settings>username>Properties. I then clicked on the Advanced tab and under the Advanced Setting, Shell showed* bin/true*. I changed it to *bin/bash*.  I'm not sure why I did it although something I read in the past may have twigged my action.  

Not an easy solution and totally lucky.  Unless of course what I did will work for now but pose problems later on.

---

