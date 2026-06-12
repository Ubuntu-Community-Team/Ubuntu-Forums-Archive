---
title: "Help again."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by wasteoftime on 2007-02-02
My first post was yesterday and i had a few problems and was considering giving linux as a whole a miss. It wasn't the challenges of hardware etc that had me frustrated it was the simple things that just seem stupidly complex that gets me!

I'm a noob so bare with me please.
My new problem like my other one is or rather should be simply solved!!!! But so far has me baffled.

How do you create a new user account?

I tried going into the manage users/group window and pressing '+ new', i fill out the details then 'ok'. Then i restart, as logging out didn't do it the first time, log back in as root and my new user has disappeared.

The help kindly supplied in ubuntu says to do what i'm doing but what i'm doing doesn't work!

I feel like i'm missing something. thanks in advance

---

### Post by danielph on 2007-02-02
Firstly it is not the best practice to log on as root. I am guessing you are doing this as you cannot log on as the user you created when you installed Ubuntu?

What you are doing sounds correct. You just need to add the user and enter a password twice and this should create a user. Logging off should then give you the ability to log on as this new user. No reboot is required.

There are 2 ways of creating an account - the way you tried and from the command line.

If you still have problems try this method

1. Open up terminal (Applications, Accessories, Terminal)
2. Make sure you are at root by typing "su" followed by the root password. If you do not know the root password you can type "sudo su" and your user password
This is an example of how to create a user called test1

3. Type
```
useradd -m -G users,audio,video,scanner -s /bin/bash test1
```You can then check in the user manager an account has been created.

---

### Post by wasteoftime on 2007-02-02
Managed to do it with the gui though for some reason it was harder than it should have been.

When i clicked "+ new" in the dialog box it for some reason added a new group with the same name as my user account of which it had not added the new user account to.

All i did was delete the new group and added the user account to the users group and it seems to have worked.

I'm happy i've got the account running as i know its better not to use root and its my fault for forgetting the old accounts password, but i'm not sure why i had to do what i've done and don't know if i've done it right!

Its fair to say i'm even more confused as when i started! Though i'm glad i didn't have to use the cli as that text looks even more confusing and i definately don understand it! Thanks though Danielph much appreciated.

---

