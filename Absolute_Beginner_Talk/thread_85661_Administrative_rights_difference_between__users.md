---
title: "Administrative rights difference between  users?"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2005-11-03
I have just installed Ubuntu and find it quite friendly , from reading some post in this forum I understood that login as root is not advisable . I'm not really sure what 'root account' means so i figured it might mean the user created during installation, lets call it User 1.  I created another user, lets call it User 2. I find though that a lot of the administrative tools simply do not work with this user 2.  I click on Synaptic Package Management,it prompts for password and then ....nothing. I click on Language Selector and ....nothing . When I switch  back to the root user  (User1)everything is cool and running smoothly  . I switch back to User2  – again nothing works , i try different sudo apt-get commands, I get no reaction. What's going on?:confused: :confused: :confused:

---

### Post by hashimoto on 2005-11-03
For information on root/sudo/users, see: [https://wiki.ubuntu.com/RootSudo?highlight=%28CategoryDocumentation%29](https://wiki.ubuntu.com/RootSudo?highlight=%28CategoryDocumentation%29)

---

### Post by Schmots on 2005-11-03
Here is an explination.

your user1 is not root.  root is root.  however ubuntu randomly creates a root password so without purposful manipulation you can't log in as root.

user1 is in all the neccesary groups to use sudo.  sudo allows that user to run as root for just that command.   Much more secure.  have no fear running as your user1 it is fine.  However kudos for trying to be more secure, most people don't care

---

### Post by UbuWu on 2005-11-03
You can give user2 administration rights by going to system -> administration -> user and groups. Then select a user and go to preferences -> rights and then select administrative rights.

---

