---
title: "Need help with .bashrc"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-26
There are 3 different bashrc files that I can see.

bash.bashrc
dot.bashrc
.bashrc

What's the difference between them ? I need to add some path variables to .bashrc but I'm not sure which file to edit and how exactly to go about it. I'd really appreciate some help. Thanks!

Another question pops into my head. How do you log in as root user ?

---

### Post by heimo on 2005-07-26
If you want to change it per user, make the change to ~/.bashrc (~ is your home directory). There's also .bash_profile (or something like that), but I never remember which is used for what - open those files to see. System wide settings files are found under /etc/

Root user is disabled by default in Ubuntu. You can use sudo to run commands with root privileges - (sudo [command]) the password is same as for user that was created during install. If you insist logging in using root account, you can set its password using sudo and passwd. To keep yourself and your system safe, don't use root when not neccessary. :) (Just a friendly advice.)

---

### Post by grofaz on 2005-07-26
Got it covered. Thanks for your post!

---

