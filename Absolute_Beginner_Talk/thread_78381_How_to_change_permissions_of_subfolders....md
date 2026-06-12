---
title: "How to change permissions of subfolders..."
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by Mandor on 2005-10-18
I never thought that I would ask such a stupid question, but since I use Linux as primary OS only after Breezy, I have a question on a matter I though is clear.

The question is: How can I change the permissions for all subfolders and files, contained in a folder, other than do it manually for each one.

Thanks in advance

---

### Post by chinaski on 2005-10-18
when it happened to me that after changing permission to one folder all subfolders and other content were still locked i did:

sudo chmod -R 777 folder

and worked

---

### Post by Mandor on 2005-10-18
10x, I actually didn't know the command for changing permissions - I could man it if I knew. In the Ubuntu Guide it's describred only changing permissions through GUI.

---

### Post by Mrtn on 2005-10-18
I don't know how either, I just login as root if I want to change something I am not allowed to change :D

---

### Post by chinaski on 2005-10-18
I'm not a command line expert either...

I only know two commands to change folders and files permission:

chown and chmod

but don't ask for the difference :D

---

### Post by Murgle on 2005-10-18
chmod changes the file permissions, who can do what to the file.  
chown changes the files owner.

---

### Post by davmac on 2005-10-18
It not too bad once you get used to it.

The difference? chown changes the owner of the file and chmod changes the... er... mod... er... no, the read/write/execute privileges of a file.

So if I have a file that I own and I want to reassign it to another user I just type "chown newuserid filename".

Now if you want to change who can read, write or execute a file then you need the chmod command. There are a number of different ways of using the command. Have a look at the examples at [http://catcode.com/teachmod/](http://catcode.com/teachmod/)

HTH,

Dave Mac

---

### Post by ChrisTheGeek on 2005-10-18
Hi,

There is unfortunately no way in the Gnome GUI to do recusive permission changes.

The reason, as I understand it, is that designing a user interface that copes with the expected behaviour is difficult, and people can't seem to agree on what the expected behaviour should be.  This is because you typically want to set permissions for directories differently to files - particularly the execute flag which is needed for directories but should be used sparingly for files.

For now, you need to drop to the command line and use chmod as already mentioned.

---

### Post by BLTicklemonster on 2005-10-20
Hey kids, guess what? If you go:

$ cd /usr/bin/
$ chown -R username /usr/bin/

then you can't get back into do any sudo stuff!!! Because if you try, you get an error message that says:

Failed to run /usr/bin/x-terminal-emulator as user root:
Child terminated with 1 status

!!! 

Isn't that just cool as ... no. It's not cool. It's actually kinda sucky.

Um, how do I undo this?


(yes, you are allowed to "LMAO" at me all you want on this one! Point fingers, and email a link to all your friends, too. I earned this one.)

---

### Post by Murgle on 2005-10-20
try just plain chown -R root\: /usr/bin and that should put things back to normal... or you could

cd /usr/bin
chown root\: sudo 
and you probably want to repeat for gksudo and gnome-sudo and possibly sudoedit

---

### Post by BoyOfDestiny on 2005-10-20
[QUOTE=Mandor]I never thought that I would ask such a stupid question, but since I use Linux as primary OS only after Breezy, I have a question on a matter I though is clear.

The question is: How can I change the permissions for all subfolders and files, contained in a folder, other than do it manually for each one.

Thanks in advance[/QUOTE]

I think everyone has to ask this at one point. I made a thread in Dapper suggestions about this:

[http://www.ubuntuforums.org/showthread.php?t=75834](http://www.ubuntuforums.org/showthread.php?t=75834)

Just to keep it on track, I do chmod 755 -R

---

### Post by BLTicklemonster on 2005-10-20
[QUOTE=Murgle]try just plain chown -R root\: /usr/bin and that should put things back to normal... or you could

cd /usr/bin
chown root\: sudo 
and you probably want to repeat for gksudo and gnome-sudo and possibly sudoedit[/QUOTE]


I'll do it when I get home. I did go and change permissions in properties and I got a gksudo error that time, so I see where you're going with that. I appreciate your help, Murgle.

( I've been Murgle-ized? )

---

### Post by patrick295767 on 2005-10-20
[QUOTE=BLTicklemonster]Hey kids, guess what? If you go:

$ cd /usr/bin/
$ chown -R username /usr/bin/

then you can't get back into do any sudo stuff!!! Because if you try, you get an error message that says:

Failed to run /usr/bin/x-terminal-emulator as user root:
Child terminated with 1 status

!!! 

Isn't that just cool as ... no. It's not cool. It's actually kinda sucky.

Um, how do I undo this?


(yes, you are allowed to "LMAO" at me all you want on this one! Point fingers, and email a link to all your friends, too. I earned this one.)[/QUOTE]

is the subject of permissions, is it ppossible to run a bash sh in super user mode from a regular user in order to mount stuffs 
like mount -t vfat /dev/hda3 /mnt/hda3 
for instance ??

thank you !!

Patrick

---

### Post by Murgle on 2005-10-20
there are two oprions that I see, either use sudo when launching the script or use gksudo in the script for everything that needs root.  then you will get a popup for your password but can run it as normal user.

Edit:
BLTicklemonster: yes indeed you have been Murgle-ized... Muhahaha

---

### Post by patrick295767 on 2005-10-20
[QUOTE=Murgle]there are two oprions that I see, either use sudo when launching the script or use gksudo in the script for everything that needs root.  then you will get a popup for your password but can run it as normal user.[/QUOTE]

u then mean that the password that i have to enter is the user password ... 

like 
#!/bin/bash
sudo mount -t mount -t vfat /dev/hda3 /mnt/hda3
___
 
 
Would then ask me a password that is the one of the user ?
Am I right ??
 
 
thank you very much for ur quick reply .

patrick

---

### Post by Murgle on 2005-10-20
if you are going to put the sudo directly in the script then use 'gksudo' that will make the same window that pops up before loading apps like synaptic.  that way you can input the password, and yes it is the surrent users password.

---

### Post by BLTicklemonster on 2005-10-20
[QUOTE=Murgle]try just plain chown -R root\: /usr/bin and that should put things back to normal... or you could

cd /usr/bin
chown root\: sudo 
and you probably want to repeat for gksudo and gnome-sudo and possibly sudoedit[/QUOTE]


bill@ubuntumonster:/usr/bin$ chown root\: sudo
chown: changing ownership of `sudo': Operation not permitted

Either method.
:(

---

### Post by Murgle on 2005-10-21
what do you get when you look at sudo with the graphical window?  who owns it, I know that user should own it, but just check and while you are there make sure that the execute option is checked... Also try and see if you can change it in the window.

---

### Post by BLTicklemonster on 2005-10-21
I own it and I can change read write and execute on owner group and others, and execute has been checked all the time.


file group is root

---

### Post by Murgle on 2005-10-21
I know this doesn't really solve the issue, but it might solve the problem... try to reinstall sudo and see if that works

---

### Post by BLTicklemonster on 2005-10-21
I'll try, but don't you have to be root to do stuff like that?

---

