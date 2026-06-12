---
title: "File permissions on peer-peer network"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by rogerwn on 2007-07-13
I am setting up a peer-peer network for an African school and want to give r/w permission to all users on the supervisor's PC to a folder called /home/userfiles (already created). I think chown might be useful but can't quite see how!

Each PC has two users: the 'install' superuser and a 'desktop' user called userNN where NN is the last two digits of the PCs hostname number.

Many thanks

---

### Post by Rocket2DMn on 2007-07-13
I think in this case each supervisor's login needs to be set on each computer as an administrator/superuser.  Then they can ssh or VNC to any computer needed and make their modifications.

---

### Post by wormser on 2007-07-13
You want to use **chmod** to set the permissions of a folder.  Another method is right click on the folder> Permissions tab> change them to your needs.  This way would probably be easier for you now. 

More on [permissions]("http://linuxcommand.org/lts0070.php").

---

### Post by annda on 2007-07-13
i would suggest using groups: make the folder r/w accessible to group "students" and make sure all the other users belong to that group too - you will have to create it on all the computers first.

---

### Post by Rocket2DMn on 2007-07-13
I don't think chown and chmod are the best options.
You probably want the PC user to own the files and have the full r/w/x access to it as necessary, but do you want EVERYBODY to be able to r/w/x?
If you want only the administrators to access everything, then they need to be working at an administrator level, without opening the files/folders to everybody.

example of problems:
chown might give problems to regular users, plus it seems you want multiple administrators.
chmod will open your files to World (in the user-group-world of permissions) and could create security problems.

edit: I think the problem with "groups" is that you have to setup each administrator for that group on each PC and ensure that all files created in the /home/userfiles folder belong to that group.  However, it is an option.

---

