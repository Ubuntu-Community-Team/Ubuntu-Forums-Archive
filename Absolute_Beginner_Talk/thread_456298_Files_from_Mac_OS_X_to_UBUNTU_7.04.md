---
title: "Files from Mac OS X to UBUNTU 7.04"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Kirkgrk on 2007-05-27
I just installed Ubuntu desktop 7.04 on my PC. I would like to know if there is a way to transfer files from my MAC os x to the Ubuntu computer. I have already configured it to be able to transfer from ubuntu to mac os on the mac itself via folder sharing. If there is a way, please explain how it can be done. Thank you for your time!

---

### Post by stimpack on 2007-05-27
I have lent my macbook to someone at the moment, so I am afraid I cant be specific, but, you can enable SSH on the macbook, then access the macbooks files in Konquerer with ssh://macbooks_ip. 

Or you can enable ftp on the mac, few options, the mac has a nice dialog its in the sharing/firewalls section.

---

### Post by Kirkgrk on 2007-05-27
Ok  ill give it a shot. i notice that if im logged on to my account and try to transfer files from the mac to the "root" account,  it wont let me do that. but if i try to transfer from my mac to my account while im logged on to it  it will let me. Thanks!

---

### Post by Kirkgrk on 2007-05-27
Actually  this is what i want to do.  
use the ubuntu pc as a "server" so i can store and share my files
I want to be able to keep the ubuntu pc on all the time.
if possible, not to connect a monitor.
i have 3 hard drives from a xp os with files already on them and want to be able to share and store files on them using ubuntu os from my imac.  


please tell me if this is possible. Thanks!

---

### Post by alastair on 2007-05-27
If you have a file browser window open on Ubuntu, you can "right-click" a folder and select :

 - Share folder

and choose to share e.g. in the Windows "SMB" way.

The MAC should be able to see this share on the network and allow you to transfer files.

---

### Post by Kirkgrk on 2007-05-27
> **alastair said:**
> If you have a file browser window open on Ubuntu, you can "right-click" a folder and select :

 - Share folder

and choose to share e.g. in the Windows "SMB" way.

The MAC should be able to see this share on the network and allow you to transfer files.

  right  im able to do that only if the file was created by the account that is logged on.   most if not all of my folders are under the "root" account and when i try to drag and drop a file using my mac to ubuntu   it wont let me. says i dont have user rights or something like that.

---

### Post by Kirkgrk on 2007-05-27
Is anyone able to further help me?  Do i have to format my hard drives in order to share them with my imac?  I want to be able to transfer files from and to the ubuntu desktop from my imac. what file format do i have use to be able to share with my imac?

---

### Post by stimpack on 2007-05-27
Setup an SSH server on ubuntu. This way round is a little harder because OS X is kinda basic and finder is very poor. Would need a program like Fugu on the mac to drag drop files then.

---

### Post by alastair on 2007-05-29
> **Kirkgrk said:**
> right  im able to do that only if the file was created by the account that is logged on.   most if not all of my folders are under the "root" account and when i try to drag and drop a file using my mac to ubuntu   it wont let me. says i dont have user rights or something like that.

If you have a folder that you want to "share" but it is
owned by user "root", you can change ownership.
[COLOR="Red"]
However, do this only for folders you create (not system
ones).[/COLOR]

So, if you have a folder :

/images

and you want to make it owned by you :

 - open a terminal - menu/accessories/Terminal
 - In terminal - type : sudo chown <your login>.<your login> /images

e.g.

sudo chown fred.fred /images
or
sudo chown fred.fred /shared/videos/
etc.

You should then be able to right-click it in the file browser and "share".
 the relevant folder(s).

As long as you connect to the share as "your your name" from the MAC, 
you should be able to drop files in.

Good luck.

---

### Post by Kirkgrk on 2007-06-01
> **alastair said:**
> If you have a folder that you want to "share" but it is
owned by user "root", you can change ownership.
[COLOR="Red"]
However, do this only for folders you create (not system
ones).[/COLOR]

So, if you have a folder :

/images

and you want to make it owned by you :

 - open a terminal - menu/accessories/Terminal
 - In terminal - type : sudo chown <your login>.<your login> /images

e.g.

sudo chown fred.fred /images
or
sudo chown fred.fred /shared/videos/
etc.

You should then be able to right-click it in the file browser and "share".
 the relevant folder(s).

As long as you connect to the share as "your your name" from the MAC, 
you should be able to drop files in.

Good luck.



Thanks  ill give it a shot. been too busy with other stuff and didnt have a chance to try anything else.

---

### Post by Kirkgrk on 2007-06-01
> **stimpack said:**
> Setup an SSH server on ubuntu. This way round is a little harder because OS X is kinda basic and finder is very poor. Would need a program like Fugu on the mac to drag drop files then.


Ok thanks for the suggestion. its worth a try!

---

