---
title: "Unable to access user folder on server from Win Client"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Mike S. on 2006-03-21
Hi,

I'm working through my next issue:

1.  Click on "My Network Places" from Win Client.
2.  Click on daddy58-(that's my user name on the server) from Win client.
3.  Click on File, New, and Folder on Win client.
4.  Message returned on Win client, "Unable to create the folder 'New Folder.
5.  Win Client indicates "Access denied"
6.  (2) files are displayed in the \\server\daddy58 from the Win Client
     ".bash_profile" and ".bashrc"

The same stitution occurs from the \\server\homes as well.

I'm logged in as daddy58.

For the life of me can not figure out how to allow new folders to be created.

I've done the following for each user:

You must add the users who need to be able to log in to the server and read and write the files. 
Click Administration, Users and Groups, and add a new user. 
To add a password for the user: 
select Applications, Accessories, Terminal. 
Into the terminal screen that pops up, 
type sudo smbpasswd -a username, replacing username with the name of the user you just created. 
When prompted, enter a password. 
Next, type sudo /etc/init.d/samba reload and press Enter (this reloads the file-sharing software, which you have to do whenever you change a user's status). 

I've read through the Samba how to on Unbuntu forums, as I'm new to linux, actually this is my first attempt, I don't understand all the terms like mounting shares, not even sure I need to mount shares.

I did create a public folder and able to create new folders from Win clients.

Feed back from a previous post suggested to do the following; however, I don’t understand how to do it.

“You mena you want to create a folder like /home/user for example? Perhaps you just forgot to use sudo to do that?”


Thanks,

Mike

---

