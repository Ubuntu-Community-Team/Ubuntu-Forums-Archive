---
title: "2 questions regarding file transfer/permissions"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Heretic Monkey 0 on 2007-07-12
I have 2 questions regarding the file permissions on a seperate physical hdd in my system, as well as transfering files from another computer on my network.

First, i can't seem to set the "read and write"  permission for my slave hdd on my computer.  I can access and copy my files from my "Spare" hdd, but i can't delete them or modify them.  I've tried right-clicking and setting the properties, but it says "sorry, couldn't change the permissions".  I'm logged in as an admin (at least, i should be) and i don't know the sudo command to try and do it from the terminal.

Second, how can i transfer files from a windows box to my linux box if they're on the same network?  I used a simple file sharing procedure to transfer files from this box (used to be windows) to the other box (still is windows) since they were on the same router, but that technique doesn't seem to work with this one.  I've tried typing in "\\your-***********" in the address bar, but it can't find it.  Is there a way to directly transfer files (massive file sizes) from a windows box to a linux box on the same router?

Thanx in advance for the help, and i apologize if any of these questions have been posted before.  I didn't see anything in my search.

---

### Post by FleetAdmiral74 on 2007-07-12
There is a command, something like sudo nautilus, which will give you gui admin privs. THat might allow you to right click and change permissions, do a quick search to make sure thats the right command though.

---

### Post by annda on 2007-07-12
welcome!

i said goodbye to windows some time ago, so sorry if this advice is too sketchy. i hope you can use it anyway. the first step is to know what to look for, so here go my two cents:

Q1: is it a disk formatted under windows? i suspect NTFS file system, which is read-only under linux without special drivers. which version of ubuntu are you using? you can put it in your user profile here in the forums, so it will be easier to give you the right advice. here's a guide with screenshots for feisty:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Q2: to enable communication between windows and linux you need to install samba:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

i don't use it so i can't help you more. but if you have problems you can try searching for samba. for example here:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by wolfen69 on 2007-07-12
to answer your first question:
```
sudo apt-get install ntfs-3g ntfs-config
```
then restart.

Applications-->System Tools-->NTFS Config

---

### Post by bradleyd on 2007-07-12
you are trying to do this in nautilus I assume. A quick way to do this is from command line type:
```
sudo nautilus
``` This will launch nautilus as root and then you should be able to change or move files on spare hdd. The correct way to do this is by changing permissions to the files and directory's. Let's say you have a directory name my_vacation_pics/.  First you should see who owns this directory and what group. You can do this by typing:
```
ls -al /mount-point-of-spare-drive/my_vacation_pics
```
you should see results something like this:
```
ls -al my_vacation_pics/
total 8
drwxr-xr-x  2 user group 4096 2007-07-12 16:05 .
drwxr-xr-x 31 user group 4096 2007-07-12 16:05 ..

```
As you can see user has read, write, execute. group and other have read,execute. Of course user and group will be different. Lets change ownership of that directory to you.
```
sudo chown HereticMonkey.HereticMonkey /mount-point-of-spare-drive/my_vacation_pics
```
now when you look at the directory again:
```
ls -al my_vacation_pics/
total 8
drwxr-xr-x  2 HereticMonkeyr HereticMonkey 4096 2007-07-12 16:05 .
drwxr-xr-x 31 HereticMonkey HereticMonkey 4096 2007-07-12 16:05 ..

```
Now we need to allow read, write, and execute permission to that folder for you.
```
sudo chmod -R 775  /mount-point-of-spare-drive/my_vacation_pics
```
This will change the directory and all its contents to read, write,execute for owner and group and read,executable for other. You should be able to(as long as your are logged in as HereticMonkey)delete files or create new ones in my_vacation-pics/. You can recreate this for any of the files and directory's on the spare drive.
There are many other ways to get files off the Windows machine,I think the easiest way to transfer files from you Windows box would be to share a folder on your Windows box and make it accessible to Everyone. Put all of your files you would like to transfer over to Linux machine, and use samba to browse share.(you can do this from Places ->Network menu if you are using Gnome)Then drag and drop.  you can download putty and scp for Windows and secure transfer files to the Linux machine.
Good luck,
Brad

---

### Post by lbelloq on 2007-07-12
1. Press Alt-F2. That'll open a window. Type "gksudo nautilus" and press ENTER. Type your account's password if asked. That will show you a file browser window with root privileges.
2. From the Run dialog of your Windows box type "\\[ip]\shared_folder" and press ENTER. It will ask for a username and password. Provide them and you're ready. Remember that you'll have to config Samba in your Linux box and open the appropiate ports in your firewall.

---

### Post by Nezing on 2007-07-12
Annda,I have been trying for weeks to **write** to my Seagate external drive,which is formatted to ntfs.I clicked on the link-page you gave,where it says writing to ntfs under Ubuntu.Once again,I get **permission denied**.I have tried many,many options on the forum,given by lots of helpful members,such as yourself,and all to no avail.People keep informing me that it is a **bug **in Ubuntu,and will be fixed upon the release of Gutsy (October).Others have said that if my external drive was formatted to Fat 32,it would work.I will not do this,as my drive is crammed with media files,and I do not have a few "boxes" of blank dvd discs to copy everything,then format.Plus it would take forever.I am now just going to wait.

Thank you for your effort. :)

---

