---
title: "Help me Share files locally between users"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Bright Hammer on 2007-04-21
Hi, I am looking for some info on how to share a folder locally with all the users on the PC not on a network. I have one pc that the family uses and i want to store all of our pictures in a location where everyone on the pc can get to them. Ideally I would like to put links(shortcuts) to the share on everyones desktop. below is what i did.


1.I made a new group called share
2.I added all the local users to the group including root
3.I created a folder call share on root of the file system
4.I tried to change the permissions on the folder but i was unable to make share the owner
5.I changed the group to share and gave them create and delete rights
6.I gave others create and delete also.
7.When i tried to make a link it said that i didn't have permissions


Please let me know what i am doing wrong so i can get this working. Maybe i don't understand permission correctly so if you can point me in the right direction i would appreciate it.

---

### Post by Crosbie on 2007-04-22
Just a guess: try making it as a new user called 'share' too?  Create the shared folder in that user's home space rather than in the root of the filesystem.  Just allow others read/write/execute permissions?

Just a shot in the dark suggestion, I'm no expert.

---

### Post by vanadium on 2007-04-22
This should be just a matter of setting the proper permissions. You would need to create a dedicated directory and give it read and execute permissions (if you do not want the shared directory to be writable by anyone. For convenience, you could create a symbolic link to that directory within each user' home directory. Then, it would just show up as a normal folder in their home directory.

All this obviously must be "installed" by the root.

sudo -i  ##converts your prompt to a root prompt
mkdir /share
chmod 550 /share
ln -s /share /home/user1  ##repeat for each user
...
exit

---

### Post by Bright Hammer on 2007-04-23
Thanks for the help on this vanadium. I will try when I get home.

---

### Post by Bright Hammer on 2007-04-25
Thanks for the help that worked. But I did have to tweak something a bit. When I created the links I had to change the permissions on them because they were owned by root. But it is working great thanks for your help. Maybe in the next version of ubuntu they will make this easier.

---

