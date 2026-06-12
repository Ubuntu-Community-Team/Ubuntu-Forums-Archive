---
title: "glabally change permissions to drives and or folders and all their subfolders"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Donkeyman on 2006-10-18
Is there a way of changing the permissions of entire drives or directories so I can actually write to them?

I read somewhere to try 
sudo chmod 777 /directory-i-want-to-changer-permissons-of
but this doesn't seem to work

---

### Post by Arby on 2006-10-18
```
sudo chmod **-R** permissions-you-want /path/to/directory
``` the -R flag means recursive, i.e this directory and all subdirectories. For other options type man chmod.

However be careful what you set the permissions to. Make sure you understand what you are doing before changing them. For example setting permissions for a whole drive to 777 means absolutely anybody who has access to your system can read/write/execute everything on that drive. This may or may not be what you want.

chmod is definitely the command you want for altering permissions so if it's not working we need to look into why. Give us the details of exactly what you are trying to do, what commands you've used, what errors you are seeing etc. What drives or directories are you trying to change permissions on?

There is a nice introduction to the permissions system here[http://www.linux.org/lessons/beginner/l14/lesson14a.html]("http://www.linux.org/lessons/beginner/l14/lesson14a.html") click next through the next couple of pages as well

---

### Post by mcduck on 2006-10-18
Also keep in mind that system directories have certain permissions, and they shouldn't be changed. You should keep all your own stuff inside your home dir (and there you have permissions for everything anyway)

---

### Post by Arby on 2006-10-18
Yeah, basically what I was trying to say is tell us exactly what you want to do and people will make suggestions about the best way to achieve it

---

### Post by Donkeyman on 2006-10-18
I read that I need to create a file in /etc to disable ipv6 globally on my system, however I can't save a new file to that directory so i tried
sudo chmod -R 777 /etc/modprobe.d
it comes back with
sudo: /etc/sudoers is mode 0777, should be 0440
and doesn't seem to change the permissions

also now that seems to come when i try to change the permissions to any directory

Have i broken something?

---

### Post by ajgreeny on 2006-10-18
Why can't you use sudo to copy the file to /etc?  Make the file you need and save it in home then from your home directory *sudo cp filename /etc/filename*.  This should work without any problems as far as I can see.

---

### Post by mcduck on 2006-10-18
yes, that's exactly what I was talking about..

instead of changing permissions of system files/dirs so that you can write to them as normal user you should use sudo when you need to modify anything outside your home dir.

So instead of chmodding /etc to write a file there you should use 'sudo gedit' (or 'sudo nautilus' or whatever you want to do) to create the file with as root..

Chmodding /etc changed the permissions for some system files that _really_need_to_have_certain_permissions_.. I think you could try booting in safe mode and chmodding them back again, but that's going to be hard as some files need different permissions than others (/etc/sudoers, for example)..

---

### Post by Arby on 2006-10-18
> **Donkeyman said:**
> I read that I need to create a file in /etc to disable ipv6 globally on my system, however I can't save a new file to that directory so i tried
sudo chmod -R 777 /etc/modprobe.d
it comes back with
sudo: /etc/sudoers is mode 0777, should be 0440
and doesn't seem to change the permissions

also now that seems to come when i try to change the permissions to any directory

Have i broken something?
This is what mcduck was referring to, /etc has specific permissions for a reason. Various elements of your system expect these permissions and can't operate if the permissions are wrong. For this reason the permissions of /etc should not be changed. If your system has refused to change the permissions on /etc/modprobe.d then it is trying to protect you from yourself. You may have got a few things slightly wrong but the situation is not unfixable so don't panic.

Your system seems to be unhappy with the permissions on /etc/sudoers so lets check those first. Please do the following at the commandline
```
cd /etc
ls -l
```this should give you a full listing of the files in that directory (it will be quite long). Find the line that relates to sudoers and copy paste it here. The first part of that line is the permissions. Actually I've just thought you could try this
```
ls -l | grep sudoers
```which should return just the lines in /etc that relate to sudoers

For future reference if you need to create a file in a system directory use sudo like this
```
#to create a file
cd /etc #for example
sudo nano -w file-to-create
#the -w means write mode as opposed to read only
#write the file you want to create then hit ctrl-X to save, it will ask you to confirm. hit y then enter 
#likewise to edit an existing file
cd /etc 
sudo nano -w existing-file
and edit accordingly
```

---

### Post by Donkeyman on 2006-10-18
cheers guys, that's a lot of help. Am learning my lesson here slowly...

---

