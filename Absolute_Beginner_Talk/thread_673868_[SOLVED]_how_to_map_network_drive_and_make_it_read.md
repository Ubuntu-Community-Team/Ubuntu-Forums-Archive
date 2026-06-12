---
title: "[SOLVED] how to map network drive and make it read/write ?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by oedha on 2008-01-21
Dear All,

i have a problem in mapping a network drive.....
My server has a public shared folder with no username and no password, it shared in windows shared format, the address is \\citserver\shared
I want to make it map in my edubuntu.......

first....i did : places - connect to server ( and the shared on citserver folder appears on the desktop )
the problem using this way : firefox and gimp can't save to it since the link was not appear on their save dialog box(even after i bookmark that network address on nautilus). but i have no problem in OO
this folder is read/write

then i tried to use smbfs........first, i made /media/x
and put this line to fstab : //citserver/shared smbfs rw 0 0
all application can show this mapping link on their save as dialog box but........the problem now......this folder is read only.........
i also changed it to 777 by chmod(no effect)......

this problem appears when my student asked me how to change the desktop background using their own pictures which save on that drive and tried to save their pictures to their network folder.

Question : how to make it map and the access is read/write for all user ???

thank you
~E~

---

### Post by foolsh on 2008-01-21
this could be many different things
first run 
```
sudo nautilus
```
then navigate to your /media folder and right click the x folder you created go to the permissions tab and change every folder access to create and delete and change file access to read/write

your fstab line looks incomplete here is mine username and password omitted
```
//192.168.1.2/BigShare    /media/BigShare    smbfs    username=*username on windows computer*,password=*password of username on windows*    0    0
```

now make sure the shared folder on the windows computer lets others read/write you'll have to access to computer directly to do this just right click the folder and check under sharing that read/write permissions are enabled also make sure the folder is not read only on the windows computer
if you have another windows computer you can check this by accessing the share from that computer and see if you can create a new folder

---

### Post by Thund3rstruck on 2008-01-21
First of all I would use CIFS instead of smbfs and also there is no uid value. The uid=myUserName should mount the share in that user context so if you enabled rw then you will inherit the appropriate permissions based on your server.

---

### Post by oedha on 2008-01-22
thx for the reply.....
but still i can't make it read/write ...except if i use sudo on terminal
but if i want to save from firefix....it can't

---

### Post by oedha on 2008-01-27
First...i would like to say sorry.....
actualy it's my mistake since i didnt notice the server setting at the beginning.

the map wasn't work because i didnt look at the server folder setting
and it was 
drwxr-x-r-x nobody nobody shared

then i went to the server .....i did 
chown -Rf root.root /home/shared
chmod -Rf 777 /home/shared

on the client i added a new line on /etc/fstab
//192.168.1.100/shared /media/x cifs rw,uid=root,gid=root,file_mode=0777,dir_mode=0777,noperm 0 0

now...it's working....everyone can read/write/delete on it and we have drive x:

thanks all
~E~

---

