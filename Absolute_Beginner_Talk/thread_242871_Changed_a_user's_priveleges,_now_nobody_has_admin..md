---
title: "Changed a user's priveleges, now nobody has admin."
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-08-24
Ok, this stinks.  I let my roommate use my computer, but I was sick of him doing admin. stuff, so I changed his priveleges.  Uh, my priveleges were also changed while changing his.  Now whatever user I log onto, I have no admin. rights.  Oops.  This has to be an easy question to fix.  I use Dapper Drake.  Thanks.

---

### Post by dannyboy79 on 2006-08-24
Well Ubuntu comes with no admin account enabled by default so I don't know what you mean by a user previously had admin privalages. You use the sudo command to get temporary admin privalages. If you want to enable the root account so you can log in as root you'll have to gogle it cause I don't know how to do that, I wouldn't ever suggest logging in as root though, you can screw up your whole computer! What are trying to do that requires admin? Just use sudo as I said.

---

### Post by anaconda on 2006-08-24
Select the 'recovery mode' boot option in your grub, and it will boot to a text mode, with root rights. Then repair your problem.

can't remember where the list of sudoers is, but add yourself to that list, or you can just give root-user a password, and then you can boot as a root..

---

### Post by anaconda on 2006-08-24
And if you want that your roommate can't boot to recovery mode, it can be prevented.. and again can't remember how. Should be easy to find

---

### Post by BarFly on 2006-08-24
> **anaconda said:**
> Select the 'recovery mode' boot option in your grub, and it will boot to a text mode, with root rights. Then repair your problem.

can't remember where the list of sudoers is, but add yourself to that list, or you can just give root-user a password, and then you can boot as a root..

Yes, I found the recovery mode you mentioned.  However, your instructions of "repair your problem" doesn't really help much as I don't know how to do that.  This is absolute beginner talk...

Thanks, though.

---

### Post by BarFly on 2006-08-24
Right now I would just be happy with restoring any users rights to get at root with gnome, whether myself or my roommate.  I know I have to boot into recovery mode and then do "something."

Yes, Dannyboy, by "admin," I meant root--  used to Win.

I will worry about limiting my roommates access once this is done.  Here is a thought--  can I simply reinstall Dapper Drake, or will it find my previous changes and go with that?

Thanks again!

---

### Post by Spookster on 2006-08-24
```
adduser *yourusername* admin
``` should do the trick. This adds you to the 'admin' group which, by default, can run any command as root through sudo.

---

### Post by FuriousLettuce on 2006-08-24
*Note: the above only works in recovery mode*

---

### Post by anaconda on 2006-08-24
Yep.. sorry. dont remember where the sudoers-list is..

but one way to "repair" the problem is to give "root" a password. 

type:

passwd

and give a password when asked.
Next boot normally, and give username: root and the password you just made. Now you can do whatever you want to do.. you have admin rights. (could be dangerous)

EDIT: the adduser ... is better advice. Just make a new user with admin rights..

---

### Post by FuriousLettuce on 2006-08-24
In fact, probably the best idea is this:

```
usermod -g admin username
```

where username is your username. This will add your username to the admin group. Again, you must be in the recovery mode to do this. It is better and more secure than activating the root account.

---

### Post by BarFly on 2006-08-24
> **Spookster said:**
> ```
adduser *yourusername* admin
``` should do the trick. This adds you to the 'admin' group which, by default, can run any command as root through sudo.

Thank you so much!  I knew there was an easy way to do this but I am butt stupid as far as Linux goes.  Thanks also to FuriousLettuce for clarifying Spookster's post (although when you posted it I was already in recovery mode), and to anaconda for pointing me in the right direction!

This is why I like Ubuntu!  There is always someone to answer your question without having an attitude trying to make you feel inferior because they know the OS better than you.

Edit:  just a typo I saw.

---

