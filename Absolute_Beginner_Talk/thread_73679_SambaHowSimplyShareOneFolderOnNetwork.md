---
title: "Samba:HowSimplyShareOneFolderOnNetwork?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-09
apt-get install samba   [done]
smbpasswd -a user       [done]
/etc/init.d/saba restart   [done]

now ???

thx

---

### Post by patrick295767 on 2005-10-10
(I use rox-filer (not nautilus))

Thank you !!

---

### Post by UbuWu on 2005-10-10
[http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)

---

### Post by patrick295767 on 2005-10-10
[QUOTE=UbuWu][http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)[/QUOTE]


Thank you very very much !!

I managed !!

_______________
(mount -t smbfs //192.168.196.44/d /mnt/win -o username=XXX -o password=xxx
if using windows XP or windows 2000
you can use

mount -t smbfs //192.168.196.44/d$ /mnt/win -o username=XXX(administrator
only) -o password=xxx)

---

### Post by patrick295767 on 2005-10-10
now : target, to let users be able to mount smbfs
---------------------------------------------------




"cd
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd

Substitute your Windows username and password in the commands. No one else except root would be able to read the contents of this file.

Once that is created, you would modify the line in the /etc/fstab file to look like this:

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpasswd 0 0

You can also use the credentials option in the smbmount command for security reasons. That command would look like this:

smbmount //servername/sharename /mountdirectory -o credentials=/home/myhomedirectory/.smbpasswd
"


----------------------------


I did that to hide my smbpassword in the /home/user/.smbpasswd
(+ stuffs  as above in the /etc/fstab)
but I try as user and it says : 
cannot find mount point (with smbmount)

& mount is only allowed by root



-------------
Is there someone who could help a bit for this next step ?

thank you very much !

Pat'

---

### Post by Jussi Kukkonen on 2005-10-10
this is from memory, so could be wrong:
```
sudo chmod +s /usr/bin/smbmnt
```
(this overrides normal user privileges for smbmnt, which is the program actually doing the mounting)

---

### Post by patrick295767 on 2005-10-11
[QUOTE=Jussi Kukkonen]this is from memory, so could be wrong:
```
sudo chmod +s /usr/bin/smbmnt
```
(this overrides normal user privileges for smbmnt, which is the program actually doing the mounting)[/QUOTE]


Yeah, i did that ...

sso the user should do : 
$ smbmnt //10.x.x.x/user /mnt/user_mnt  -o username:dflsmqflmd -o password:fsqdqfds
   
but it's not possible to do so.

Please, how the user could mount a smbfs ?

tahnk you very much

---

### Post by UbuWu on 2005-10-11
[QUOTE=patrick295767]Yeah, i did that ...

sso the user should do : 
$ smbmnt //10.x.x.x/user /mnt/user_mnt  -o username:dflsmqflmd -o password:fsqdqfds
   
but it's not possible to do so.

Please, how the user could mount a smbfs ?

tahnk you very much[/QUOTE]

Probably like this:
$ sudo smbmnt //10.x.x.x/user /mnt/user_mnt  -o username:dflsmqflmd -o

---

### Post by Jussi Kukkonen on 2005-10-12
You can just keep using mount as you did before -- it will call smbmnt.

---

### Post by patrick295767 on 2005-10-12
thank you very much. I 'll let you know this evening my progress !

---

### Post by patrick295767 on 2005-10-12
[QUOTE=Jussi Kukkonen]You can just keep using mount as you did before -- it will call smbmnt.[/QUOTE]

Maybe, it's tooo much questions... a lot a lot ...
I tried, it's workign great the samba. 
I am then accessing the Home directory of the user !
  
That's damn nice. But I have an addtional folder, /mnt/sda1 (external harddisk), could you let me know how to share it too to the network (and rights eventually) ?
  (If you find time)
  
I am newbie, and it's not sooo easy to install linux, to make it work. After 5weeks, now, I can achieve some results with linux but it's very long to master all the possibilities of the operating system.
  
Thank you very much !!

Patrick
    
--
Linux gave a very nice & fast new life to old Pc's that I have !!

---

