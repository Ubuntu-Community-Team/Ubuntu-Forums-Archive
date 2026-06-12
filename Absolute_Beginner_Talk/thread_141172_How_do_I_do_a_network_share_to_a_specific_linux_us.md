---
title: "How do I do a network share to a specific linux user?"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-07
Is it possible to do a network share for /home/john/mysharedfolder to a user peter (assuming peter has a useraccount on the system) over the intranet, without using samba? For the client (peter), how does he access the shared folder (assuming peter's system does not have a GUI insterface)?

Thanks !

---

### Post by Pragmatist on 2006-03-08
You can just make them both members of the same group and give the group the required permissions.  Then peter could ssh into the system with the shared folder.
1.Create a group (I'm calling it "shared")```
groupadd shared
```
2. Add peter to this new group "shared":```
usermod -G shared peter
```
3. Change the group on your shared folder:
```
chgrp shared /home/john/mysharedfolder
```
Now you just change the group permissions to what you want the members of the group (you and peter in this case) to have.  so if the permissions of mysharedfolder are: -rw-rw----  and its owned by "john" and group name is "shared"  Then peter could read and write to this file just like john can.  Others can't do anything with this file.
Make sure you install **sshd** which is the secure shell daemon on the machine with the folder you want to share.  peter's computer will need to have an ssh client.  Then you could give peter the IP address of your machine. You can find it with ```
ifconfig
```  He will then use that IP address like this (assuming the ifconfig command shows that your machine's IP is 192.168.0.1):

In a terminal he types: ssh peter@192.168.0.1  
Then he is asked for a password, he gives it, 
and Voila! he is logged in remotely and can do whatever he could do if he were logged in locally.  He has all the same restrictions of his account.

---

### Post by deBaas on 2006-03-08
Why not samba? You could also install a ftp deamon.

---

### Post by ryanVickers on 2007-05-24
Yes, I would use a smb connection, or if you need to share the whole computer, use ssh.  for more info on this, see: [http://ubuntuforums.org/showthread.php?t=448529](http://ubuntuforums.org/showthread.php?t=448529)

it's how to set up ssh or ftp (they say ftp is easier, but I strongly disagree)

---

