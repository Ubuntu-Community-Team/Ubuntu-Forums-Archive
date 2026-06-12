---
title: "cannot open display"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by doughardy on 2007-06-06
hi everyone 
                Im an absolutly week old  newb to the  linux operating system but need a little help on some thing in stuck on.

 i have a lan setup with 3 windows xp and  1 linux  ubuntu 2.6.20-15-server  started ssh server on linux  and a client on xp  i can acess  linux  remotely using SSH Secure Shell Client (showing up as like dos prompts eg me@ubuntu:~$ )  and view all the folders in the linux system using  SSH Secure File Transfer Client.
if  i type the ip address of the linux machine i see the apache web page you know  the one where its says   it works  lol .
 
now here  the problem  if im doing it right     i want to edit the apache2.conf file to change the root docs etc  so i enter this
 
    me@ubuntu:~$ sudo gedit apache2.conf

    Password:xxxxxxxxxxxx

     cannot open display: <   this is what i get guys  so  any help with this  would be really appreciated thx all

---

### Post by Seisen on 2007-06-06
Let me understand this correctly. You are using SSH from your Windows Box into you remote Ubuntu Box, correct. Since most SSH sessions are text based you will need to use vim or nano instead of gedit.

---

### Post by doughardy on 2007-06-06
i have  used   sudo nano etc/apache2/apache2.conf      that worked it opened  the conf file but i see  no  text to edit yet just going to have a look at the  commands  on the bottom of page

---

### Post by zero-9376 on 2007-06-06
Gedit is a graphical editor (like notepad on windows). In order to use this you could run an xserver like xming on your windows computer and that way you would have graphical apps which run on ubuntu but are displayed on the xp client. This setup is probably overcomplicated for what you are doing though. As Seisen stated you could use a console based text editor (in my opinion nano is the easiest of those installed by default for new users) or alternatively you could simply copy the file to your windows machine, edit it in notepad (or whatever text editor you prefer) and then upload it back onto the linux machine. Not the most elegant solution but it works and you dont have to use console editors or install x.

---

### Post by doughardy on 2007-06-06
thx very much guys all sorted now ,  must do alot  more reading now :p


                               MUCH APPRECIATED:popcorn:

---

