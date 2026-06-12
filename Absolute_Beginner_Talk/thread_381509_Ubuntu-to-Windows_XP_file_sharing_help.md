---
title: "Ubuntu-to-Windows XP file sharing help"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Seski on 2007-03-11
Hello. I am new to the whole Linux scene, and I only know most basic commands. I need some help with fire sharing from Ubuntu to Windows XP Pro.

Every time I go into the network directory in Windows, I see the server, but when I double-click on it, I get a message saying that the "Parameter is wrong" and says the server doesn't accept remote file sharing if I right click and go into Properties. Can someone please walk me through it? I'm on Ubuntu right now, so anyone willing to help, I'm ready.

I run 6.10, BTW.

 -Thanks

---

### Post by guysmiley25 on 2007-03-11
Have you setup samba correctly?

Try this page here [http://ubuntuguide.org/]("http://ubuntuguide.org/").

Go down to where it has stuff about samba. Also this page might help you with some other things as well.

---

### Post by Seski on 2007-03-11
I'm a newbie, and it went over my head

---

### Post by seshomaru samma on 2007-03-11
well the first step is install samba
open a terminal (applications>accessories>terminal) and paste this command:
```
sudo apt-get install samba smbfs
```
next paste these lines into the terminal ,pressing enter after each one :
```
sudo mkdir /home/group
sudo chmod 777 /home/group/
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf
```
a new windows will open with the smb.conf file
look for this line:

```
...
;  security = user
...
```
replace it with this:
  ```
security = user
  username map = /etc/samba/smbusers
```
then add this at the end of the file:
```
[Group]
  comment = Group Folder
  path = /home/group
  public = yes
  writable = yes
  valid users = system_username1 system_username2
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup
```
save the file
run these two commands in the terminal (pressing enter after each one(
```
sudo testparm
sudo /etc/init.d/samba restart
```
if you get any errors ,post them here

---

### Post by Wartooth on 2007-03-11
What parts of those commands have something that needs to be replaced with the individual's username.   Like 

security = user   

Does "user" need to be a username?

And also:
 valid users = system_username1 system_username2

Looks suspicious to me as well.  I only ask this as I have gotten tripped up by simply copy/pasting in the past, having neither paid close enough attention to what I was copying nor been warned about changing things to reflect my username or computer, etc. 

Thanks :)

---

### Post by guysmiley25 on 2007-03-11
It's depends on what you want to do. This is why I pointed to that other page. Are you wanting to just share a folder that can be accessed by windows machines? Do you want the windows machines to have just read access or read/write access?

I'm not sure on seshomaru samma setup mysef, not knowing too much about it. However to answer your questions,

"security = user" is just that. You do not need to enter a user name. This is a option, I think you could also have something like security = all.

"valid users = system_username1 system_username2" I have not ever used. However I would expect that it is the system user names that you would put in here. But I am not sure if it would be your ubuntu machines users. Or your windows users. I would expect that it is your ubuntu users.

Good luck!

---

### Post by Seski on 2007-03-11
Thanks, it works perfectly now.

---

### Post by civicsi99 on 2007-03-11
noob question...........does gedit ingore anything between semicolons? ive seen quite a few copy code sections with the semicolons before instructions.
example -- ; put your name here

so can you just copy and paste the whole text that someone provides into gedit? thanks.

---

