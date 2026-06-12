---
title: "new user doesn't appear in users+groups"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by xadder on 2007-03-05
I just installed xubuntu edgy on my IBM T43, using an installation user pete1. All went reasonably okay, and I added a new user pete, which I had intended for day-today work. I wanted to change some settings (groups, permission to use network, etc.) for pete, but I can't see how to do that. 
when I call up System -> Users and Groups, I just see petei and root. 

cat /etc/passwd shows that pete has been added, and a home directory has been created. Why don't I see this in the Users+groups tool, and how do I change this?  Thanks

---

### Post by saphil on 2007-03-06
have you ever actually logged in as pete?

---

### Post by xadder on 2007-03-07
Yep, that's no problem. I can log in as Pete, or do "su pete" from  petei. It just seems to be the "users+groups" thing which doesn't see this.

---

### Post by saphil on 2007-03-07
did you put the pete user in through the command line or the users+groups dialog?  I have had students 'adduser' a new user and then have that user not be available in the dialog.  Like there was a step they missed or something.  I am looking for answer to the problem, but as you have noticed, it is hard to search for an issue that you define differently than somebody else did.  What we did in lab was just try to produce a new user (with a different name) through the users+groups dialog.  We did it that way because there was a finite amount of time to do the lab.  This is a work-around and not a solution.

How does this work for you?

---

### Post by xadder on 2007-03-07
I used the graphical way: System -> Users and groups -> Add User

I just tried adding another user though, and found something interesting:


Simple new user - default setttings - this worked - and shows up nicely in the GUI. 
When I do cat /etc/passwd  or /etc/group I see the new test user, formatted
exactly the way the pete is. 

Then I remembered that I gave a lower UID to pete, 500 instead of the default 1001 or whatveer it was.
So I tried the test user with UID=506. That disappeared!

The GUI doesn't like UID < 1000 by the look if it!

(I preferred to have 500 since I run unison a lot, and my other machines disks have this UID. I learned that
unison is easier if one doesn't have to fiddle with different UIDs on different computers.)

---

### Post by saphil on 2007-03-07
It is true.  Thre are very few places to get lost in the process. 

Ahhh...  I think the lower numbers are for "system" users.  There are a lot of processes that have user accounts and they are not visible in the dialog either..  I do believe you are on to something here.

So the solution is to let the UID be set automatically by the system or use it to make "invisible" users.

---

### Post by saphil on 2007-03-07
so the real question is "how can the user+groups dialog be set to view users below 1000" or what script controls the read-out.  

This is obviously a way to keep untrained people from looking at their dialog and exclaiming "Where did all these USERS come from?!  I've been hacked!!" and deleting all the system users.  People like you who are not beginners would just as obviously be frustrated.  Marvelous!

I bet, if you logged in as root and ran startx, all the users would be visible to you.

---

### Post by xadder on 2007-03-07
Well, if I do "su root" and gksu users-admin it doesn't help. I can't remember how to get into the state where startx is used. My normal startup takes me to the login screen, and this won't allow root.

I found that there was a bug-report written about this, but haven't found the bug yet. I also
see in the help manual that settings in the key "/apps/gnome-system-tools/users/show_all" 
will show the system users too. If only I knew where to change that...!

---

