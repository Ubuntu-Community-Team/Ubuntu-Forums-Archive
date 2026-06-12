---
title: "Mount remote dir as my home dir"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by pacer on 2005-09-05
misfortune - need help
Hello Friends .
My HDD died yesterday.And i thought this is the end :(
For now i'am unable to by a new one. But i need to do my work. Usually i'm working with remote servers using SSH. And i not worry about my local data.
Luckily i have a DVD with Ubuntu , which allow me to boot my laptop from live CD.
I've tried to boot it from this DVD. And .... it works. Now i'm happy .
Running "dhclient" i have now access to network and internet , as you can see :)
I think i will bay a new one HDD at the end of this month. But until that day i have to work somehow ...
Now i have only one user created for me . and his name is "ubuntu".
I can setup my Email client , Messenger etc . But then i'll turn off the power of my laptop i'll lose all settings . And next time i have to repeat all to setup required enviroment.
I think i can try to create a new user "Pacer" with his home dir somewhere at network servers .
I'm able to access an NTFS server where i have a special place only for me "server1/personal/pacer/" ( i need to provide my password first of all to access this place)
The question is ...
How do you think is this a good temp solution in my case...
Then i'll start my laptop i'll create a new user "PACER"
after that i hope i'll mount the remote ntfs dir at my home dir. I'm not sure if it is possible. Please tell me how should i do it.
in other words . i want a /home/pacer to be really placed at server1/personal/pacer/ ( this is a place on windows server).
In general , is it possible ? or i just have a "rich fantasy"
If yes , please describe all necessary steps ...
Thank you very much for you collaboration.

---

### Post by wmcbrine on 2005-09-05
In general, it is possible. Though it would probably be better if the remote directory was on a Unix system and shared via NFS.

In practice, I'm not sure. You need smbmount, and I don't think it's part of the live CD. Maybe another distro would have it? Or... can you buy or borrow a USB thumb drive?

---

### Post by skoal on 2005-09-05
Mounting a remote partition as /home using NFS isn't too difficult, what is however, is the fact that you said it's an _NTFS_ partition.  I do not believe you can write to an _NTFS_ partition yet, and that would be hazardous when it's your /home drive...

\\//_

---

### Post by wmcbrine on 2005-09-05
It wouldn't matter that it was NTFS if it was remote (over the network). In that case it's an SMB filesystem, as far as Linux is concerned. (Or even NFS, if you put up NFS on the server. But I don't think the OP has that kind of access.)

If you're willing to forgo the idea of remote-mounting your home directory, and just sync manually, you can use smbclient (like command-line FTP, but for SMB), or even Nautilus (try "Places", "Network Servers").

---

### Post by pacer on 2005-09-06
Thank you .
I copied all files (including hidden) from /home/ubuntu/ into //server1/personal/pacer
I mounted a remote dir using mount smbfs at /home/ubuntu/.
Closed the current X session using Ctrl+alt+Backspase.
Reloggined the ubuntu user for home directory renew.
But then i tried to statx . i get an error . Something like that " ... can't lock .Xauthority file ...."

Why . I've checked i can read/write into /home/ubuntu

---

