---
title: "setting different access"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-24
I finally have the server set up to where I can create and share folders on the server hdd and map to them with the windows computers. Now I am trying to set up where various computers have access to various folders on the server. All access would be R/W or none.

There are currently 3 folders (A, B, C) and 3 sets of users (1, 2, 3).  All users have access to folder C.  User 1 has access to A & C.  User 2 has access to B & C.  User 3 has access only to folder C.

I have the 3 folders set up but the access to all is the same.  I believe it has something to do with "groups"?  

Can anyone point me to a "HOW-TO" or something that would cover it. I searched the forums and could not find anything that helped.  New to Linux and the forum so it is probably there.

Thanks.

---

### Post by alan34 on 2007-11-24
This might not be perfect but you should get the idea.

sudo adduser A
sudo smbpasswd -add A

sudo adduser B
sudo smbpasswd -add B

sudo adduser C
sudo smbpasswd -add C

sudo smbpasswd -add 1
sudo smbpasswd -add 2
sudo smbpasswd -add 3


sudo /etc/init.d/samba restart

Go to the directory under the directories A, B and C

sudo chown A.A A
sudo chown B.B B
sudo chown C.C C

sudo chmod o-rx A    (Removes access for others - not member of group A)
sudo chmod o-rx B
sudo chmod o-rx C

ls -l     should look like

drwxr-x--- A A  somenumber A
same for B and C


sudo gedit /etc/group


You should find groups A B C at the bottom of the file the add your users 123 to the correct groups.

for example
A:x:1000:1        (number[1000] will be different do not change it!!!!!!)
B:x:1001:2
C:x:1002:1,2,3

The smilies above should be a letter x dont know why they are like that:(

Which I hope should give you what you want but you will have to play with /etc/samba/smb.conf
as well I would look on the official Samba website for more information.

All the best. I am going out for some beer now my brain hurts it is only small:confused::)

PS may have to 
sudo chmod g+w A[B][C] to give members of the particular groups write permissions.

Do not use any command like rm -rf /anything. Always either "man" or "info" any commands you are not sure about

---

