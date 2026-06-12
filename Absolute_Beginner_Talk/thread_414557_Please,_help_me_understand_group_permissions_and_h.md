---
title: "Please, help me understand group permissions and how to secure my files"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Jh00 on 2007-04-19
Hi there.

I'm in process of setting up a new PC running Ubuntu for my family, but before that, I wanted to test some stuff to see where I am heading to.

So, I wanted to know if other users could access my files in my home dir. So, after creating the initial ubuntu user (julio), I created another user (teste). Then, I created a few files in julio's dir , logged into teste and tried to "less file.txt" to see if he could. Ok, he could open it.

Ok, it would be expectable, since "file.txt" is -rw-rw-r-- . But I wanted teste to access all my files but that one. So, first I set the file to 660 , in hoping that teste would fit into the "all others" group, but teste could still open the file.

So, I wondered: "Ok, teste must be in the same group as julio". Checking the Users and Groups panel in Feisty, I noticed that teste was not in the group named julio. So, why teste could open it?

Then I checked /etc/group and /etc/passwd and noticed these lines:
```

julio:x:1000:1000:julio,,,:/home/julio:/bin/bash
teste:x:1001:1000:teste,,,,:/home/teste:/bin/bash

```

Now comes my doubt: julio and teste have the same GUID (1000), and that's probably the reason why teste still could open that file. Why is that? 

a) Why ubuntu hasnt put teste in his own group, and instead, set him as part of the same group as me?
b) Why I cant see teste in julio's group in "User and Groups" panel in gnome?
c) Suppose that I would like to block access from anyone else to all my personal files but one, what should I do?
d) And, in another way, if I wanted to allow access to everything, but one file? 

If someone could answer those 4 questions, maybe I can get a better understanding on how to handle user and groups permissions in the future.

Thank you very much!
Jh00

---

### Post by lamalex on 2007-04-20
you may want to read here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) and see if it helps any

---

### Post by Jh00 on 2007-04-20
Thank you for replying!

However, after reading the contents of that link, I can say that I already knew all that. I know a little bit of Linux since 1997, but I dont comprehend the "behind the stages" working of some things, like those 4 questions. 

It is like... I know how to press the button, I know where the button is, I just dont know what it is for.

EDIT: BTW, I spent over an hour googling for those answers before writing my first post. Just to let people know that I tried.

---

### Post by Jh00 on 2007-04-22
bump. I really wanted to understand it..

---

### Post by Jh00 on 2007-04-23
I still waiting for some kind soul to answer my questions, but I wanted to clarify one thing: when I asked

> 
a) Why ubuntu hasnt put teste in his own group, and instead, set him as part of the same group as me?


I meant this: wouldn't it be better if Ubuntu created one new group for each new user? In this way, it would be a lot easier to specify who would have access to your files or not.

For example: considering 3 users: bob, peter and jane , each one in its own group. Bob could easily add peter to his group, while jane could add peter to her group as well but still keep bob out of her home directory. 

I think this is a privacy issue of some concern. I thought that, by default, Ubuntu would isolate each user in its own home dir by default. If I wanted to grant access to someone to my files, I would need to add them to my group or do something else. At least, that's the whole idea I got about "linux being secure". 

In the real world, consider these examples:
a) Ubuntu deployed to a school - students want to work on their homeworks, but don't want other students to view their files;
b) Ubuntu at home: sister wants to write a journal, but she doesn't have a single idea about permissions, and she surely wouldn't want her brother to peek at it;
c) Ubuntu at home: husband wants to save some porn in its home dir, but his wife uses the PC as well and is extremely jealous... :-)

That's why I think that the default behaviour should be to isolate each user for the other.

It this approach is not the best one, someone could tell me why so - at least I would understand the principles behind this policy.

Thanks again. Let's see if anyone answers me.

---

### Post by Jh00 on 2007-04-25
Is this the appropriate forum to ask this? If it isn't, please, could someone move my post to the correct forum? Thanks.

---

### Post by nvteighen on 2007-04-25
If you go to terminal and write "ls -l", what does it says?

---

### Post by Skrynesaver on 2007-04-25
Redhat uses this approach (one group per user), however if you don't want other users in your group to see a file, chmod 600 filename.  You can edit group ownership, and indeed create new groups in /etc/group, another related tip is umask, if you ```
umask 066
``` you have to explicitly allow people to read files.

---

### Post by thornomad on 2007-04-25
I don't really use linux on the desktop that much these days ... but in server-world, depending on how you add the user seems to influence the user's group ... perhaps teste and julio are in the "users" group ?  Have you tried looking at:

id teste
id julio

or

groups test julio

Are they the same ?  Not sure, though, why the graphical version of ubuntu would do that necessarily.

---

### Post by psusi on 2007-04-25
You are correct, the primary gid for teste should NOT be 1000, it should be 1001.  This is the problem.  The user teste is, in fact, a member of the julio group.

---

### Post by Jh00 on 2007-04-25
Finally someone came to the rescue! Thanks for the postings guys.

I'm not at home now, so I can't post the output of the suggested commands. But something occured to me: I created the new user "teste" using the GUI interface in Gnome. So, now I'm in doubt if this is really an Ubuntu  policy (of setting all users into the same group) or a bug in the gnome "Add user" system.

How could we verify this? Perhaps someone could add a user using terminal and see what happens?

---

### Post by psusi on 2007-04-25
Which version are you running?  Feisty?

---

### Post by Jh00 on 2007-04-25
I'm using a fresh install of Feisty Fawn.

Ok, here is an update:

I was reading the man pages of adduser and noticed this paragraph:

> 
By  default,  each  user  in  Debian GNU/Linux is given a corresponding group with the same name.  


So, that answers my question if this "feature" was indeed an Ubuntu policy or a bug in the "Users and Groups" management of Gnome - indeed, each new user should have their own group.

I tested it by running in console:  "adduser teste2" and voilá, a new teste2 user was created, along with a new teste2 group, like I expected.

Then I tried to create an "teste3" user by using "User and Groups" from Gnome, just like the first time, and strangely enough, it created a new group for him this time... And all subsequent users were created just like it should.

I don't know what triggered this, but it is very strange that the first user that I created didn't have its own new group. I will try to reproduce this again tomorrow, in another PC, and see what happens.

Thanks for now!

P.S. - BTW, after I created a new user (along with its new group), protecting the files from the new user was a breeze! All I had to do was to make my home dir "drwxr-x---" and we were set.

---

