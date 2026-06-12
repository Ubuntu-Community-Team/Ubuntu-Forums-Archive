---
title: "Can't run any admin tools (Update Manager, etc)"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Skychrono on 2006-05-07
Hm.

Alright, so I installed Ubuntu 5 a bit ago, then left to college. I get back and see there's an update to Ubuntu 6 - alright. So I go into the Update Manager to download it. But it won't do that. It won't run system apps through the graphical (GNOME?) interface. Firefox runs, but I can't go to the update manager, Users and Groups thing, Login Screen Setup... etc. None of the admin things run, though the "start bar" says "Staring Users and Groups."

If it's important, I have a dual setup with Windows 2000 & Ubuntu on the computer currently. I'd go to "Disks" and confirm that the three partitions are there, but it's not starting - just like the rest of the admin programs.

Did I set up Ubuntu wrong or something? Why won't programs start?

FYI, I couldn't run the admin tools before I went to college, but didn't think much of it at the time.

Edit - in posting this (on my other computer) I found out that I suck at everything. I was trying to sudo mkdir /media/windows so I could mount a Windows drive, and I don't seem to have permission on this name. I guess I know less than I thought.

Edit2 - should I just install Ubuntu 6 over this? I got a LiveCD iso.

Sorry for all the trouble!

---

### Post by annda on 2006-05-07
for security reasons, admin tools don't just start when you click on them. the system must be sure you have sufficient privileges (dapper aka ubuntu 6 is clever enough to ask you for the password via a dialog window, previous versions - as far as I know - just aborted).

the best way to find out what's going on is to open the terminal window and type something like:
```
sudo apt-get update
```
it will ask you for your password and proceed to update its database of available packages.

if you have a problem with this, something might be wrong with the system. but if that works fine, it means you have all rights you need to run and configure your system. however, for some tools you will need to search the forums and find exactly the commands/program names to type.

also (if the above worked for you) you can try upgrading to dapper by typing in the terminal:
```
gksudo "update-manager -d"
```
that should make some things easier, at least the administration via GUI.

---

### Post by 5-HT on 2006-05-07
[quote=Skychrono]...I can't go to the update manager, Users and Groups thing, Login Screen Setup... etc. None of the admin things run, though the "start bar" says "Staring Users and Groups."

...Did I set up Ubuntu wrong or something? Why won't programs start?

FYI, I couldn't run the admin tools before I went to college, but didn't think much of it at the time....
[/quote] 
Do you remember if you did an 'expert install'?
In Breezy, if you do an expert install your user is not added to the sudoers file.
What is the sudoers file? Well, it sets permissions on who can use sudo and what  they can use it for.

It seems like your user is not in the sudoers file.
Here is a great link by Mustard that walks you through how to add a user to the sudoers file: _[http://www.ubuntuforums.org/showpost.php?p=901128&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=901128&postcount=4")_

Even if you did not do an expert install, if this issue is occuring because your user is not in the sudoers file, the above link should hopefully fix the problem.

Hope that helps.

[quote=annda]dapper aka ubuntu 6 is clever enough to ask you for the password via a dialog window, previous versions - as far as I know - just aborted. [/quote] 
As far as I know, all versions of Ubuntu will give you the graphical prompt to escalate privileges to run the admin tools. 
A small issue with Breezy was that if the user did an expert install, there user was not added to the sudoers file. 

I'm not sure, but believe this has been fixed in Dapper. 
However, if someone is doing an expert install, they should really know how to add a user to the sudoers list anyway. 
It is an 'expert' install after all (the standard install does a great job, and also lets you edit the partition table manually).

---

### Post by Skychrono on 2006-05-08
Sorry, but... bump. Very stumped. :(

Edit: Allllright, it didn't refresh. Anyway. Thanks! Just about to try this.

---

