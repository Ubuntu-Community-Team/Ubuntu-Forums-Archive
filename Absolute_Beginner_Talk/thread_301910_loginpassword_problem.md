---
title: "login/password problem"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by benner on 2006-11-17
I have 2 machines linked through a router.  one is running xp and the other has ubuntu.  in 'workgroup computers' in windows, i can see the ubuntu machine but i can't access the files.  it asks for a password and the login/password that i have set up on that machine doesnt work.  when i go the other way, i select 'network folders' in konquerer (i am running KDE 3.5) and select samba shares, i see the XP machine.  when i select it, i get a 'could not connect to the host' error.  the XP machine has no login/password and there are plenty of files that have been shared.

the XP machine is set up for dual boot and also has kubuntu running on it.  i don't often run it so it's important that i get the sharing set up with the windows machine and the other one, but even when i have linux running on both, they see eachother but can't connect and share files.

i know there are a million other posts about this and and read a bunch but can't find one that answers my problem so far.  suggestions?  thanks in advance...

---

### Post by Swab on 2006-11-17
Do you mean they are connected via a switch?  If they are on different sides of a router then they won't be able to see each other.

---

### Post by benner on 2006-11-17
i don't quite understand your question.  they are both connected to a router (ip sharing router) that connects to the internet.  they can both see one another and both appear in the same workgroup (MShome) but can't connect to one another to share files.  the XP machine asks for a password but then the password doesn't work.  the ubuntu machine just won't connect.

---

### Post by nyinge on 2006-11-17
Do you have the xp firewall on?  If so, add your ubuntu machine's ip to the trusted list.  I had the same problem, but like I said, I added my ubuntu's ip as trusted domain.  I'm using ZoneAlarm though.  Not too sure how to configure the XP's firewall, though it should be easy.

Edit:  I havn't tested the other way around -- grabbing Ubuntu's files from XP.

Edit2:  I didn't really explicitly share any folders on XP.  I saw C$ (for C drive), D$ (for D drive), when I click on the XP machine in Ubuntu.  I've read somewhere that those names with '$' are implicitly shared for admin purposes. 
Anyway, after I opened the C$ folders, I was confronted with a login window where I put in my username and password that I set up for XP.  I can then see all files/folders inside C.

Edit3:  (not too sure!)  I think you'll need to configure SAMBA services on Linux machine for windows to see files on it .

---

### Post by benner on 2006-11-17
thanks.  didn't work.  i turned off the firewall completely (zonealarm) and made sure the windows one was also off.  still can' connect.

---

### Post by nyinge on 2006-11-20
You said XP got no login/password.  Then I think you're logging in with" Administrator" as login and no password.  Try connecting with "Administrator" as username on your Linux machine and leave blank for password.  

If that doesn't work, try the following:


Try creating a new user with its own password.  Choosing the type of member shouldn't matter here, i.e., Admin/user/etc.

Go to the shared folder properties.  Under "Sharing" tab, check if "Everyone" has at least the "read" permission.

Now, under "Security" tab, add the new user that you just created, make sure that user at least has "read" permissions.  Note:  The user must be selected in the upper block to chance his/her specific permissions at the bottom block.

Ok, now go back to your ubuntu machine.  Fire up Konqueror.  This time, when you see your XP machine, right-click on it, and see if there's any option to access it with different username/password.  (I'm not running Konqueror, so I'd be vague here.)

See if that works.

---

