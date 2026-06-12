---
title: "server for applications game files etc.."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by EnterG on 2008-04-17
hi to all i am new at the forum!i ve never used ubuntu but i am interested to.
i ve read a lot guides and posts in here and searched a lot in the forum about 
the topic i am going to say.

i want to create a server (game application file etc....) which will have all the files (i think compressed).
i say i think because i ve seen a server like this and i know that is a linux server.
the main idea is that the client (xp client) will have only some "shortcuts" of the games apps files (for ex videos) and all this stuff will be in the server.
what i saw is that when you click sth of the above to launch it s been downloading installed and finally launched (by one click) in the xp client.
maybe the files are only shortcuts of the server and has not to be downloaded in the client.
but what about the games and the applications ?
can i do this think via ubuntu ?

i am new to this stuff and i want some help .
i ve read tutorials guides etc on how to install configure etc ubuntu (but i haven t use it yet)

i hope you get the main idea!

thx in advance keep up the good work in here ! =D>=D>

---

### Post by talsemgeest on 2008-04-18
That should be simple enough. So you want to do all of this via the network?
You should be able to do it with ubuntu server, just acting as a file server.

---

### Post by northern lights on 2008-04-18
I didn't quite get what exactly it is that requires more than simple filesharing.

NFS or Samba (since you are in a partial Windows network should do just fine (i.e. no "server" edition required)...

---

### Post by EnterG on 2008-04-18
so the answer is that i must try :

ububtu server (ive downloaded it but i don t know how to use it and configure it to the topic i described)

nfs or samba - don t know what it is and how to use it and configure it to the topic i described , where to download it 

is there a code i must create to this stuff for my job to be done ? 

told you i ve never used linux b 4 .

sorry for my silly questions ....

:confused::confused::confused:

---

### Post by talsemgeest on 2008-04-18
All right, samba is allready installed when you install ubuntu server, so everything you should need will be installed out of the box.

However, the thing that might scare you is that after you installed it, you get put in front of a command line (there is no desktop for ubuntu server.) To fix this, type ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
reboot
```

After it restarts, you will have a nice GUI desktop on ubuntu server.

Hope this helps :)

---

