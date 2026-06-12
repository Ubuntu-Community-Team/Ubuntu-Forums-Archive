---
title: "Failing to create a group-writeable directory"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by JR_UB on 2007-12-29
I am trying to create a group writeable directory. I have read material on file and directory permissions. I still do not understand what I am doing wrong. I am trying to create a directory that all members of a group can write to. If I can get it working, then in the future I can just add users to the group as needed, and then they should be able to start adding to the directory contents. Here is what I did.

*su to root first.*
$ su

*as root:*
# groupadd test
# usermod -G test jay

[I]This should have made the group call 'test' and added my user 'jay' to it.
checked to make sure.
[/I]
# members test
jay

*Seems OK.*

*make a directory to test things out with.*
# mkdir /test

*set its group*
# chgrp test /test

*change it to be group writeable*
# chmod 775 /test

*check it to be sure*
# ls -l / |grep test
drwxrwxr-x   2 root test  4096 2007-12-29 10:54 test

*seems correct. shows group write rights and group is test.*

*drop back to user mode*
# exit

*Try and create a subdirectory*
$ mkdir /test/test
mkdir: cannot create directory `/test/test': Permission denied

*try and make a file*
$ touch /test/test
touch: cannot touch `/test/test': Permission denied

I just do not get it. I created a group, added myself to it, created a directory and made it write able to that group, but still cannot create subdirectories or files in it as  group member.  I would love to get an explanation as to why it did not work and the proper way to achieve this.

My frustration level is very high on this right now.

---

### Post by blueridgedog on 2007-12-29
have you logged out/in since adding yourself to the group? 

Try issuing the command:

newgrp

---

### Post by JR_UB on 2007-12-29
OMG. That was it. After logging out and back in things worked.

Why?   Is it necessary to make the group changes to the user take effect?

---

### Post by JR_UB on 2007-12-29
OK. I just read the man page for the 'newgrp' command you suggested and now I understand. Thank you for the help.

---

