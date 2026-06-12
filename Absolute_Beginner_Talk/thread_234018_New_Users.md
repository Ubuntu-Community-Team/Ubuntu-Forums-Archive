---
title: "New Users"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-08-10
I'm loving Ubuntu it's been great so far.  I have a quick question.  I want to add a user.  Simple enough, I can do that no problem. The problem is that I want that user to have the exact same set up as me - like desktop icons, themes, firefox extensions, etc.  How can I accomplish this without manually going through everything?  I've done a lot of stuff to set it up, I just wouldn't be able to remember everything.  Can anyone help me?

---

### Post by VirtuAlex on 2006-08-10
I think you just need to copy everything (all the hidden files) from your home folder to the new user's home folder. The tricky part is that you have to change all permissions too.

---

### Post by kebes on 2006-08-11
I agree with VirtuAlex: the easiest way to create a new user that starts just like your current setup is to copy the home directory. Note that this means the two users will not be synced afterwards. Changes made to one will not propagate to the other. (Is this what you wanted?)

To copy the home dir of user "first" to user "second", and then change permissions:

$ sudo cp /home/first/* /home/second/ -r
$ sudo chown second:second /home/second -R

---

