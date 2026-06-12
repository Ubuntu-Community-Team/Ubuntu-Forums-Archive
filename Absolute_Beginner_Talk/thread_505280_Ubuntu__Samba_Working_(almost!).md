---
title: "Ubuntu / Samba Working (almost!)"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by dsewell on 2007-07-20
Hi,

I have set-up Ubuntu to boot from USB, added Webmin and Samba, and, with the exception of the issue below, seems to be working well (not bad for a first attempt at Linux!)

I am primarily using the Ubuntu box as a low-power file server, with a 500gb drive running on a Via EPAI fanless main-board.  The Ubuntu box is on a home network, and will be used as a media server (music, movies, backup photos, etc...)

I have managed to access the 500gb drive (sda1), and by using CHMOD I have changed access so that everyone has read / write access.  Except, than I can not move files from Explorer in XP.  The reason, I think, is that when I move a directory, the directory attributes are changed and I no longer have write access.  Therefore, I get a message in Windows saying that I dont have the privalages to edit the directory.

So, I have two questions:

1) How do I fix the issue and set-up Samba / Ubuntu so that I have read/write access to new directories & files added to the shared drive?

2) Is this secure?  I have not seen any firewall settings in Ubuntu.  Should I be using User accounts and Groups to access the files?  If so, any pointers?  I have three other PC's on the network so if I need to set-up Users / Groups I guess I will need to do this three times?  Yes?

What is the correct / secure way to set-up such a media / home server?  If it's using Users & Groups, how do I tie the three XP users to Ubuntu and then to Samba so that they have read/write (and move) access?

Finally, I use SyncToy to back up data on the three XP machines.  If I get the XP users set-up, should SyncToy be able to access the Ubuntu box without any problems.

Lots of questions I know, but I am very enthusiastic about the progress so far.  This seems to be a sticking point (I have read pages and pages on Samba set-up and still am having problems!)

Thanks in advance.

Dean

---

### Post by GMachine_24 on 2007-07-20
Hi: Without knowing a bit more about your set up it's difficult for me to understand exactly what your problem might be. But, I always refer people to this article 

[http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590)

because it answers most questions/issues. It is NOT, of course, a Bible or anything.

So, onward:


> 1) How do I fix the issue and set-up Samba / Ubuntu so that I have read/write access to new directories & files added to the shared drive?

Each Samba share, if you've enabled user security, must be accessed using the user name and password. Are you logged into the Samba share when attempting the transfer? I'm guessing you are, but I'm trying to cover all the bases. Also, of course, your smb.conf folder must be configured correctly.

When you add new folders and/or drives to the computer with Samba enabled, you will have to set permissions so people other than 'root' can write to the folders - if that's what you want to do. Here's the command I use:

sudo chmod 777 /foldername/*

with 'folder' being the name of your top tree folder; the 777 allows read/write access to anyone. Make sure this is what you want. If there are files in the 'folder' (or other items) that you want to share other than just additional folders, a 

sudo chmod 777 /foldername

should do the trick



> 2) Is this secure? I have not seen any firewall settings in Ubuntu. Should I be using User accounts and Groups to access the files? If so, any pointers? I have three other PC's on the network so if I need to set-up Users / Groups I guess I will need to do this three times? Yes?

First, one user on your Samba share should suffice. You just must use that name and password from each Windows machine. That user name also must be able to log into the computer on which you are running Samba - the name must have at least a user account on the Ubuntu machine.

Re: security, in the article I mentioned previously it tells you how to set up an SSH (or whatever it's called) connection. Your Windows machines will have to be configured to allow you to connect to other computers and setting up Samba allows access to your 500GB Ubuntu drive - and if you checked 'enable others access to my folders and printer' in your Windows boxes, after the brief set up for the Windows network, you should be good to go.

More generally, there is a firewall program called Firestarter that you can use on your Linux/Ubuntu machine(s). I think it's available re: Synaptic and/or the 'apt-get install firestarter' method. Of course I recommend reading up on the program's details before installing.

If you have more questions, specifics are always helpful in getting a detailed and accurate response to your questions.

It's not that difficult to do. I have three Linux boxes, each with a network drive; and three or however many Windows boxes which also have access to the network.

Good luck.

gm

---

### Post by dsewell on 2007-07-23
Many thanks for your very detailed reply.  I will try again this evening to fix this.

An update -- I changed the file / directory attributes because they were set to 'root' access only.  So, I can now access files and write to directories.  But, if I create a new directory in XP, I can not write to it because the Linux attributes are for 'root' again.

This issue also occurs when I move (drag / drop) files, because XP creates a duplicate directory when I try to move files, but then cannot write to the directory because XP does not have access writes.  If I change the attribuites in Linux for the new directory, then I can move the files.  But, by default, I can't.

I assume that I need to change either a Samba config / user config setting someplace.  But, again, I have know idea where to start!

Regards,

Dean

---

