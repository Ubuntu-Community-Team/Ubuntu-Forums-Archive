---
title: "Unable to make new subfolder under &quot;homes&quot; folder for a user"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Mike S. on 2006-03-07
Hi,

I've added users to the samba server and unable to make subfolders on the server for each individual user.  I get a message back "Access Denied".  I've look at the permissions and don't see anything wrong.  I have windows XP clients who can see the user folders and "homes" folders; however, unable to creat subfolders from the windows xp clients.

Creating sub folders off the public folder works ok.  

Any suggestions would be appreciated.

Thanks,

Mike

Here's the process I used to setup the new users:

1.  Click Administration, Users and Groups, and add a new user. 

2.  To add a password for the user: 

3.  select Applications, Accessories, Terminal. 

4.  Into the terminal screen that pops up, 
    type sudo smbpasswd -a username, replacing username with the name   of   the user you just created. 

5.  When prompted, enter a password. 

6.  Next, type sudo /etc/init.d/samba reload and press Enter (this reloads the file-sharing software, which you have to do whenever you change a user's status). 

7.  Repeat the process for every user, and then close the terminal window.

8.  Create a folder for music, videos, and other files that everyone can access. 

9.  Right-click the desktop and select Create New Folder. 

10. Name the new folder something like Public, then right-click this folder and select Share folder. Give the folder an obvious name (such as Public Share) and select Allow browsing.

11. Now open Windows Explorer on one of the Windows machines that will access the server, type \\Server in the address bar, and press Enter. 

12. You'll be asked for a user name and password; enter one of the user names you created and press Enter again. 

13. You'll then see the folders for the user on the server: 

14. The Homes folder is for files that only the current user can access.

---

### Post by el3ktro on 2006-03-08
You mena you want to create a folder like /home/user for example? Perhaps you just forgot to use sudo to do that?


Tom

---

