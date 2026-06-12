---
title: "Change default permissions for files created"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by zmod on 2007-03-09
How do i change default permissions for the files i create under gnome? It doesn't matter really if i change for all files i create in the future but right now the new files get rw------- and i want rw-r--r--.
How do i do this?

Thanks!

---

### Post by dannyboy79 on 2007-03-09
if you want everyone to be able to read the file you would use the chmod command along with either the octal values of the letter equivalents. so either 

sudo chmod ga+r filenamehere

or 

sudo chmod 0644 filenamehere

both of these will results in the same permission, I was merely telling you how to do it either way so you can learn. the g and the a stand for group and all, the + stands for adding that permission, the r stands for read. octal values are a little more difficult to explain so you should read about it to learn.

NOTE: the first 0 sets the uid or gid and you can leave off the 0 if you like and it will still work, that;s why you'll sometimes get help from others that will just tell you 644. good luck. if I were you I would read about chmod to better understand what I have just told you.

---

### Post by EnigmaStigma on 2007-03-09
> **zmod said:**
> How do i change default permissions for the files i create under gnome? It doesn't matter really if i change for all files i create in the future but right now the new files get rw------- and i want rw-r--r--.
How do i do this?

Thanks!

you wanna use umask.

if you want rw-r--r-- you can go umask u=rw,g=r,o=r
or since you've already got rw for the user just do umask g+r,o+r
or you can go umask 644

just depends on what you want to do but either one will work

---

### Post by zmod on 2007-03-09
Thank you both for your answers! Well thats right i want to change the file permissions. But thats the annoying thing. Everytime i create a file i don't want to chmod it to make the group and others able to read it. I want it to be default.

If this is what umask does where do i change this so it will affect me in my gnome GUI? When right clicking and making a new file?

Thanks!

---

### Post by EnigmaStigma on 2007-03-09
Here's what you gotta do. 

Check the properties of the folder you're creating files in. In the properties pop-up you'll see a tab that says "permissions" from that tab you can change the permission of the folder itself as well as the files within it. 

hope that helps,
Enigma

---

### Post by zmod on 2007-03-09
> **EnigmaStigma said:**
> Here's what you gotta do. 

Check the properties of the folder you're creating files in. In the properties pop-up you'll see a tab that says "permissions" from that tab you can change the permission of the folder itself as well as the files within it. 

hope that helps,
Enigma

I managed to change all existing files. But still the same problem when i create a new file. It get's the old acess with rw-------.

I can't understand how it can be so hard to perform such a simple task!

Thanks for you help!

---

### Post by dannyboy79 on 2007-03-09
> **zmod said:**
> I managed to change all existing files. But still the same problem when i create a new file. It get's the old acess with rw-------.

I can't understand how it can be so hard to perform such a simple task!

Thanks for you help!

well there are a few different places to change this, one place is in your .bash_profile file located within your home directory. another place is in the /etc/login.defs .  this can be a security risk, it's better to just set the umask for that session using what the guy said above before creating files, umask 027 or umask ga+w whatever you'd like. i believe I am correct in saying this but I am pretty new to linux so some1 else may correct  me please. i do know that umask and chmod are opposite, so chmod 777 makes a file read, write, execute for all, umask 777 makes the file NOT readable, writable, or executable by ANYONE! good luck. you can always do some testing, go to the terminal and type in umask 022 then just do touch b, then do a ls -l and i will show the permisisons of the file "b" that you just created, if you don;t like the permission, then do a umask 333, or whatever you want, then touch b again, and you can again look at the permissions.

---

### Post by EnigmaStigma on 2007-03-09
So far that's the only thing I could find out in order to change the permission in GNOME. I'm pretty new to Linux and unfortunately my UNIX class was focused on terminal use. I did try changing the umask and then creating a file in GNOME but it didn't work out. What kind of files are you trying to make?

---

### Post by zmod on 2007-03-10
Well that seem to work in the terminal! But i would like to get it readable even when i do it in the GNOME GUI. 
I do make php files for making homesites.

Thanks!

---

### Post by dannyboy79 on 2007-03-12
the umask should be effective for ALL file or folder creation. are you saying that if you were in nautilus for example, and you right clicked and you hit, create file, then it creates a text file but yet your permissions aren't according to your umask setting? they should be! According to this website, [http://www.oracle.com/technology/pub/articles/calish_file_commands.html](http://www.oracle.com/technology/pub/articles/calish_file_commands.html)
 it states: [B]Default file permissions are set with the umask command, either systemwide in the /etc/init.dev file or locally in the .profile file. This command indicates the number to be subtracted from 777 to obtain the default permissions: 
$ umask 022
This would result in a default file permission of 755 for all new files created by the user. [/B]
the link I proved is A crash course in Linux file commands for the newly initiated so you should read the entire thing if you 're new to linux. good luck

---

### Post by EnigmaStigma on 2007-03-13
It works within terminal but...unfortunantely it doesn't seem to do anything when it comes to creating files in GNOME. Still haven't figured out what's going on...

dang it,

Enigma

---

### Post by dannyboy79 on 2007-03-13
i don't know what you mean when you say you create files in gnome, gnome is simply a window manager, like kde or xfce. can you please be very specific to exactly what you are doing. also, did you do what I suggest just first by trying to use the umask command at the command line to change it for that session only? then just touch any file to see if it worked? this setting should be a system wide setting. have you gogled this issue? also, do you use the umask options within your fstab? are you writing these files to fat32 or ext3 partitions? there are many variables to take into account.,

---

### Post by chicha on 2007-03-13
Hello EnigmaStigma,

As explained above the command 
umask 022
Will set the permissions to 755 (rwx-r-x-r-x) for every newly created file.

If you run this command in a terminal, this setting will be effective for this terminal only, and until you close the terminal.

What you have to do is put this command in the relevant configuration file used by both your terminal and your Gnome environnement.

So what is this file ?

If you want this setting for a particular user only just put the command "umask 022" in the file ".bash_profile"  (do not forget the dot in front of the file name) at the root of the user's home. Create this file if it does not exist.

If you want this setting for every user on the computer (I do not recommand this, for security reasons : root user files could be read by anyone) put the command "umask 022" in the /etc/profile file

Whatever the method choosen, you need to logoff from your Gnome session and login again (no need to restart the computer) to make the changes effective.

I hope it helped !
Cheers,

Chicha

---

### Post by helpdeskdan on 2007-03-20
That is incorrect for gnome.  Turns out it's hard coded in gdm.  

Links of interest:
[https://bugs.launchpad.net/gdm/+bug/25910](https://bugs.launchpad.net/gdm/+bug/25910)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=368080](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=368080)
[http://bugzilla.gnome.org/show_bug.cgi?id=305931](http://bugzilla.gnome.org/show_bug.cgi?id=305931)
[https://launchpad.net/ubuntu/+source/nautilus/+bug/88994](https://launchpad.net/ubuntu/+source/nautilus/+bug/88994)
[http://bugzilla.gnome.org/show_bug.cgi?id=327249](http://bugzilla.gnome.org/show_bug.cgi?id=327249)

I hope to see it backported.

---

### Post by helpdeskdan on 2007-03-20
Retracted

---

### Post by dannyboy79 on 2007-03-21
> **helpdeskdan said:**
> Several people have posted various things from adding a .gnomerc to modifying the /etc/gdm/Xsession.  None of them work.  Quite the security problem.

Are you running a server and authenticating against an LDAP server with roaming profiles and wanting folders to follow ACL? If not than you don't need to be concerned about the second bug you posted! Therefore what chicha said DOES work. You have posted 2 completely seperate bugs and it is my belief that you are only doing that to provoke an arguement regarding Ubuntu and bug's being resolved. If you filed the bug and it doesn't get handled as fast as you want it than get other people to post at the bug. Apparently the one bug is already fixed in Fiesty. If you're having issues with samba mounted shares, try using the smb.conf options per this: [http://www.ubuntuforums.org/showthread.php?t=386342](http://www.ubuntuforums.org/showthread.php?t=386342)

---

### Post by helpdeskdan on 2007-03-23
Point taken.  An afternoon of frustration is no reason to start a flame.  Which link was LDAP now?

---

### Post by compmodder26 on 2007-03-23
As is pointed out above.  There is a bug that prevents any program that utilizes gnome-vfs from using a user's umask setting.  This is fixed in Feisty.  For me to get it to work I had to place my usmask command in .gnomerc.  Actually I also read that it is fixed in Dapper because it is an LTS but the developers are ignoring it for Edgy.

---

### Post by helpdeskdan on 2007-03-23
I believe you may find that this does not work for Nautilus.  Right click and create a blank file and then check it's permissions.  If I fix is released, I hope it makes edgy as I do not plan on trying feisty till it is released in April.

---

