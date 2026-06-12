---
title: "connect vista to a share"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by payneardo on 2007-05-17
Hi I have manged to get Ubuntu setup and working but when I try and connect to the shares with vista it asks for a username and password and when I enter the one for ubuntu it wont accept it

Do I have set up a differnt user or give users access to shares or type someing in the connection box in vista after tthe first fail it defaults to vistapc\username

it is also the same in osx, I have tried smb://ubuntu/sharename and it asks for the username & password but it wont accept it ???

Cheers

Dave

---

### Post by echo $USER on 2007-05-17
you need to create a samba username and password like...

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_network_users](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_network_users)

---

### Post by phr0ze on 2007-05-17
Vista has a 'bug' - I mean feature - in it. I found the answer in some blog. You need to edit the registry in Vista and adjust the compatability. Without this registry hack Vista will not properly authenticate with non-windows shares such as SMB. 

Ok, It appears that there is an official way of fixing this, but it only works on some flavors of vista. The registry edit will work on all versions of vista. It can be found here: [http://www.geeksrus.com/2007/03/17/connecting-to-mac-file-sharing-via-vista/]("http://www.geeksrus.com/2007/03/17/connecting-to-mac-file-sharing-via-vista/")

It looks like alot but all you are doing is changing a 3 to a 1 on the compatability setting. This has worked for me and Vista can now talk to my SMB network appliances.

One other solution, upgrade to Samba 3.0. Not always an option when using appliances.
Good Luck.

---

