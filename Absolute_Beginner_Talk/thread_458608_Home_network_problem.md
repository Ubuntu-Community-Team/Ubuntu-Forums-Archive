---
title: "Home network problem"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by MintabiePete on 2007-05-29
Not too sure  what has happened here , I have  4  computers  all with  ubuntu/ win 2000 pro dual boot  and have no problem  sharing  files   with  windows but as soon as I try to  transfer  files  in  ubuntu   with  gFTP  I  run into problems  , and  can only  seem to access 1  computer . When I had ubuntu 6.06 & 6.10 I could  see  all my   computers  using  gFTP  and transfer  files   from one to another  but now with all the  computers on Ubuntu 7.04 Feisty  I can only  seem to access one  computer , but in a  round about way I can transfer  files  from one to another , but it involves a  lot of  work .   Can anyone  perhaps see what I  am  doing  wrong . I would like to be  able  to see and   transfer  files  like I  did  previously  . I can ping  from one to another  with no problems , just cant  seem  to use files transfer using  gFTP .

I hope I have  explained  enough , probably not , but  I will try and give  more  information  if I can  :)

BTW this is  wired network :)

---

### Post by ukripper on 2007-05-30
> **MintabiePete said:**
> Not too sure  what has happened here , I have  4  computers  all with  ubuntu/ win 2000 pro dual boot  and have no problem  sharing  files   with  windows but as soon as I try to  transfer  files  in  ubuntu   with  gFTP  I  run into problems  , and  can only  seem to access 1  computer . When I had ubuntu 6.06 & 6.10 I could  see  all my   computers  using  gFTP  and transfer  files   from one to another  but now with all the  computers on Ubuntu 7.04 Feisty  I can only  seem to access one  computer , but in a  round about way I can transfer  files  from one to another , but it involves a  lot of  work .   Can anyone  perhaps see what I  am  doing  wrong . I would like to be  able  to see and   transfer  files  like I  did  previously  . I can ping  from one to another  with no problems , just cant  seem  to use files transfer using  gFTP .

I hope I have  explained  enough , probably not , but  I will try and give  more  information  if I can  :)

BTW this is  wired network :)

Not sure about gFTP but you can give gproftpd a try which is also GUI based and is in repositories. I use proftpd with no problem having 5 machines including 2 laptops at home, connected through one router where i guess you need to set port forwarding on NAT as your router acts as DNS server if you want to access externally.
And internally I dont need to use FTP at all Samba does good file sharing for me.

---

### Post by tact on 2007-05-30
> **ukripper said:**
> 
And internally I dont need to use FTP at all Samba does good file sharing for me.

Ya samba works fine for me at home sharing files with my wife's winXP box

---

### Post by ukripper on 2007-05-30
Never understimate Samba. It is easy to setup as well. Just go through Samba docs and you will be amazed how easy it is to setup i have even got print server setup using SMB protocol which makes evrything centralised at my home. Just rember to give appropriate permissions to each user or probably assign to to specific machines.

---

### Post by MintabiePete on 2007-05-30
I tried to set up samba  but never seem to be  able  to get it  to  work properly  ubuntu to ubuntu   files  sharing

---

### Post by tact on 2007-05-31
> **MintabiePete said:**
> I tried to set up samba  but never seem to be  able  to get it  to  work properly  ubuntu to ubuntu   files  sharing

If you followed any of the hundreds of How To: guides out there for setting up samba, complete with editing PAM files, and nsswitch files etc...   waste of time.

For simple file sharing the default samba config is fine.   Just remember that the default settings require peopel who access the shares to have a username and password.  if thats not too hard to live with then you need not edit ANY config files.  it jsut works.

you do have to set up usernames and passwords and set shared file permissions so that "others" can do what you wish them to be able to do.

I followed ukripper's suggestion and gave gproftp a shot just for the fun of it. It works very well too.  In my corporate LAN windows and linux users could get in and ftp files up or down nicely.

---

### Post by lazyart on 2007-05-31
Simple Steps to Samba Sharing:

1 - right click on a folder and share it.  Select SMB.
2 - sudo smbpasswd -a *username*
3 - sudo smbpasswd -e *username*

Username now has same permissions across the network as it would have locally for that folder.

---

### Post by steve-shinn on 2007-05-31
what essentially is the difference between those 2 command lines ie. what is each command doing ?

---

### Post by lazyart on 2007-05-31
Get ready to laugh:

-a Activates Samba sharing for that user.
-e Enables Samba sharing for the user.

There is a chance that I got the order of them backwards-- if you get an error message after -a go ahead and do -e and then -a again.  Without both it just doesnt work.

---

### Post by steve-shinn on 2007-05-31
Thanks for that lazyart .....

---

