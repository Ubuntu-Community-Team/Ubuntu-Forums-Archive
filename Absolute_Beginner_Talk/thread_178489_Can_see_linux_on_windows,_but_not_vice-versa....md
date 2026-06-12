---
title: "Can see linux on windows, but not vice-versa..."
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-17
I use samba to share files between a win box and ubuntu box.  i can access my shared folder of ubuntu in my win box, but when i try to access win in ubuntu, i really don't have a clue.  i go to Places->Network Servers->Windows Network, but there's nothing there! And yes i've enabled filesharing on my win box! ](*,)

---

### Post by jpkotta on 2006-05-17
My samba client works the same way.  I'm not sure how to change it so it just shows up, but I can get to see the Windows computer by specifying the name.  In Nautilus, Ctrl-L to get to the location bar, then "smb://foo" to browse the Windows computer named "foo".

---

### Post by user1397 on 2006-05-17
[quote=jpkotta]In Nautilus, Ctrl-L to get to the location bar, then "smb://foo" to browse the Windows [SIZE=2]com[/SIZE]puter named "foo".[/quote]
When I do this, i get the following:
[SIZE=3]**The folder contents could not be displayed.**
[SIZE=2]Sorry, could not display all the contents of
"Windows Network: foo".
[/SIZE][/SIZE]

---

### Post by joshrobinson on 2006-05-17
[QUOTE=erik1397]When I do this, i get the following:
[SIZE=3]**The folder contents could not be displayed.**
[SIZE=2]Sorry, could not display all the contents of
"Windows Network: foo".
[/SIZE][/SIZE][/QUOTE]

is there a firewall on the windows computer? maybe its blocking your request.. also make sure everything involving smb is installed in synaptic, maybe by chance you are missing a package..

also did you set your workgroup on ubuntu?


also whats the green team under your name.. did you just get that? i see you on here alot

---

### Post by user1397 on 2006-05-17
[quote=joshrobinson]is there a firewall on the windows computer? maybe its blocking your request.. also make sure everything involving smb is installed in synaptic, maybe by chance you are missing a package..

also did you set your workgroup on ubuntu?


also whats the green team under your name.. did you just get that? i see you on here alot[/quote]
-there's only the windows firewall, but i have set it to allow sharing.
-would you mind telling me which packages i would need? (there's a whole bunch when you type samba in synaptic!)
-how would i go about setting my workgroup in ubuntu? is it in smb.conf?
-about the green team thing, i think you've already seen my thread about it and posted on it :D

---

### Post by user1397 on 2006-05-18
yea my workgrup is Mshome, and it's obviously right because it works.
(only when trying to view ubuntu folders in windows, not the other way)

---

### Post by redistributer on 2006-05-18
Well there is a few things.....

1. Make sure that the user login  account your using on your linux box is on your windows box as well (for authentication).
2. Open Synaptic and make sure you have the following packages installed
- libsmbclient
- samba
- samba-common
- smb-client
3. If your new and I'm guessing you are, find a package in synaptic called tksmb
install it and create a launcer with the command TkSmb (caps sens | you can also run the command from prompt) It's a gui utility that makes it easy to browse windows networks via auth user and pass host name (or ip address) and group (workgroup) It's a great tool for usage while your learning.
4. Make sure you don't have mcaffe or symantec security center or any of that other "windows protection" crap running.
5. Make sure your firewall dosn't have the don't allow exceptions box checked. 

There is a thousand ways to connect to a windows box from linux.
If your using gnome you can go to places on the menu bar and select connect to server and change the service type to windows share.

More than likley the reason you can't browse the network from the file browser though is the fact that your not being authenticated by windows queries for some reason, (see step one)

---

### Post by user1397 on 2006-05-18
[quote=redistributer]Well there is a few things.....

1. Make sure that the user login  account your using on your linux box is on your windows box as well (for authentication).
2. Open Synaptic and make sure you have the following packages installed
- libsmbclient
- samba
- samba-common
- smb-client
3. If your new and I'm guessing you are, find a package in synaptic called tksmb
install it and create a launcer with the command TkSmb (caps sens | you can also run the command from prompt) It's a gui utility that makes it easy to browse windows networks via auth user and pass host name (or ip address) and group (workgroup) It's a great tool for usage while your learning.
4. Make sure you don't have mcaffe or symantec security center or any of that other "windows protection" crap running.
5. Make sure your firewall dosn't have the don't allow exceptions box checked. 

There is a thousand ways to connect to a windows box from linux.
If your using gnome you can go to places on the menu bar and select connect to server and change the service type to windows share.

More than likley the reason you can't browse the network from the file browser though is the fact that your not being authenticated by windows queries for some reason, (see step one)[/quote]
thanks a lot for the suggestions, i will try all of them until it works

---

### Post by EdThaSlayer on 2006-05-19
[QUOTE=erik1397]I use samba to share files between a win box and ubuntu box.  i can access my shared folder of ubuntu in my win box, but when i try to access win in ubuntu, i really don't have a clue.  i go to Places->Network Servers->Windows Network, but there's nothing there! And yes i've enabled filesharing on my win box! ](*,)[/QUOTE]
You should try using Konquerer[excuse my spelling].
You should be able to find it in your internet section where firefox is located.

After starting the program you can choose to acces your network(With me this is the only way to acces a computer running Windows)

---

### Post by djsroknrol on 2006-05-19
I had the same problem...I believe that smbfs is the part that controls windows computer views...make sure you have that installed as well...also make sure that wins is in your resolve list in smb.conf...

---

### Post by user1397 on 2006-05-19
[quote=djsroknrol]I had the same problem...I believe that smbfs is the part that controls windows computer views...make sure you have that installed as well...also make sure that wins is in your resolve list in smb.conf...[/quote]
have both of those checked :)

---

### Post by user1397 on 2006-05-19
[quote=redistributer]Well there is a few things.....

1. Make sure that the user login  account your using on your linux box is on your windows box as well (for authentication).
2. Open Synaptic and make sure you have the following packages installed
- libsmbclient
- samba
- samba-common
- smb-client
3. If your new and I'm guessing you are, find a package in synaptic called tksmb
install it and create a launcer with the command TkSmb (caps sens | you can also run the command from prompt) It's a gui utility that makes it easy to browse windows networks via auth user and pass host name (or ip address) and group (workgroup) It's a great tool for usage while your learning.
4. Make sure you don't have mcaffe or symantec security center or any of that other "windows protection" crap running.
5. Make sure your firewall dosn't have the don't allow exceptions box checked. 

There is a thousand ways to connect to a windows box from linux.
If your using gnome you can go to places on the menu bar and select connect to server and change the service type to windows share.

More than likley the reason you can't browse the network from the file browser though is the fact that your not being authenticated by windows queries for some reason, (see step one)[/quote]
how exactly would i go about doing step 1?
do you mean the samba username or my ubuntu login screen user name?
cause if its the samba one you mean, i don't have one. when i see my ubuntu shared folder in windows, i just go to start->run: \\ubuntuIPaddress
it doesn't ask me for username or password or anything, i can immediately browse through my shares. is this wrong?

---

### Post by user1397 on 2006-05-19
Man, this thread surely isn't popular around here...:p

---

### Post by dmizer on 2006-05-19
try here: [http://www.ubuntuforums.org/showthread.php?t=169660&highlight=ubuntu+serving+windows](http://www.ubuntuforums.org/showthread.php?t=169660&highlight=ubuntu+serving+windows)

it's what finally got me going correctly.

edit ... there really should be a good gui for samba config, because it's a huge pain via cli.

---

### Post by user1397 on 2006-05-20
[quote=dmizer]try here: [http://www.ubuntuforums.org/showthread.php?t=169660&highlight=ubuntu+serving+windows]("http://www.ubuntuforums.org/showthread.php?t=169660&highlight=ubuntu+serving+windows")

it's what finally got me going correctly.

edit ... there really should be a good gui for samba config, because it's a huge pain via cli.[/quote]
yes i agree!
i will read your thread many times until i can fix my problem, there seems to be many good points in there...

---

