---
title: "gutsy user in file system not in users and groups"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by grewolf on 2007-10-22
I am currently trying out Gutsy and have done a fresh install but now I have a user that I don't remeber adding in the filesystem but does not appear in the users and groups under system>administration>users and groups.  

I would either like to have it added to users and groups or delete it from the terminal.  

Any recommendation as to which the better option would be?  I am conserned as I don't remember adding this user in gutsy but from the previous install of Feisty.  

Any insight would be appreciated.  

When I did the Fresh install of Gutsy I selected guided user entire drive

If any more info is needed please let me know.

---

### Post by TeaSwigger on 2007-10-22
Honestly I'm a bit lost by your description, although I get lost often enough it might not be due to your description ;) Could you perhaps explain it this way: What is it that you see, where is it and how do you see it? What leads you to thinking there's a user? Is it a folder or...? What is it called and where is it? So on. More info please :)

---

### Post by Yfrwlf on 2007-10-30
The only way you could have an existing user aside from root and your created user showing up in "Users and Groups" is if you retained some configuration settings and did not do a completely fresh install, if that's what you're talking about.

To delete a user, you just select the user and select delete.

Certain programs may create their own users on your system in order for them to function properly.  For example, GPROFTP will create a system user for FTP traffic after you tell it the user you want to create.

---

### Post by grewolf on 2007-11-03
> **TeaSwigger said:**
> Honestly I'm a bit lost by your description, although I get lost often enough it might not be due to your description ;) Could you perhaps explain it this way: What is it that you see, where is it and how do you see it? What leads you to thinking there's a user? Is it a folder or...? What is it called and where is it? So on. More info please :)

I go to the filesystem and select the home file then I see all the users listed.  and that is where I find it.  It is a file.  I go to the places>computer and it brings up the "file manager" (I think this is what it is called).  I click on the up arrow to bring me to the top of the file system.  I then click on the home folder and see this user, or what I think is a user because I can see my user name there as well.  When I click on the user it has examples and I see all the example files like Aesop's fables.  I hope this description helps.  

I don't know if this should be under a different topic but under groups in the users and groups gui I have a sabayon admin that I didn't see before and I didn't add.  Does any one know if this is added by a program?

Sorry to take so long to check back but I have been working out of town with no access to the computer.  Thank you for all your help

---

### Post by Maestro23 on 2007-11-03
> **grewolf said:**
> I go to the filesystem and select the home file then I see all the users listed.  and that is where I find it.  It is a file.  I go to the places>computer and it brings up the "file manager" (I think this is what it is called).  I click on the up arrow to bring me to the top of the file system.  I then click on the home folder and see this user, or what I think is a user because I can see my user name there as well.  When I click on the user it has examples and I see all the example files like Aesop's fables.  I hope this description helps.  

I don't know if this should be under a different topic but under groups in the users and groups gui I have a **sabayon admin** that I didn't see before and I didn't add.  Does any one know if this is added by a program?

Sorry to take so long to check back but I have been working out of town with no access to the computer.  Thank you for all your help

Strange.   Only place I can think of that the sabayon admin account came from, is in the link below.  Does someone else use your system?

[http://www.gnome.org/projects/sabayon/](http://www.gnome.org/projects/sabayon/)

---

### Post by Yfrwlf on 2007-11-05
In your file manager if you go to your home folder and then go back one folder into home, you will see your user as well as any other users that have system accounts.  The "proper" way to see and edit/remove/add users though is by going to System > Administration > Users and Groups in order to see all these users.  If you're the only one on your system, you should see your user and root.  If a program has installed more users, or if you or someone else have, then you will see more users show up.  Tell us the name of any of these additional users if you see them.

---

### Post by grewolf on 2008-06-23
> **Yfrwlf said:**
> In your file manager if you go to your home folder and then go back one folder into home, you will see your user as well as any other users that have system accounts.  The "proper" way to see and edit/remove/add users though is by going to System > Administration > Users and Groups in order to see all these users.  If you're the only one on your system, you should see your user and root.  If a program has installed more users, or if you or someone else have, then you will see more users show up.  Tell us the name of any of these additional users if you see them.

I am sorry that I didn't respond earlier.  I have a little more experience (not much) and think I resolved the issue by doing a fresh install.  I have never seen seen root as a user in    [COLOR="Red"]/home[/COLOR]     .  Should I?

---

### Post by Yfrwlf on 2008-06-24
> **grewolf said:**
> I am sorry that I didn't respond earlier.  I have a little more experience (not much) and think I resolved the issue by doing a fresh install.  I have never seen seen root as a user in    [COLOR="Red"]/home[/COLOR]     .  Should I?

Sorry, the one user you won't see listed in /home is the root user.  In Linux, there is a heavy segregation of "system/root" files and user accessible files, for security reasons.  The root user's home directory is actually in /root.  All the other normal users who are given home directories have their directory/folder in /home, so if you go to the "users as groups" tool in system>admin and create a new desktop user, you will see their directory appear in /home.

Any way, it's not something you normally need to worry about usually except in perhaps knowing where your home is and knowing that there are hidden directories in your home folder that have dots in the front of them which hold configuration information for the programs you use, which are viewable by checking "show hidden files" in Nautilus (may have to open a new window after checking it).  That's about it really. :)

---

