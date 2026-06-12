---
title: "new to linux:nfs help!!!"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-16
hi im still learing the A,B,C's of ubuntu and linux. At the moment i'm follwing a manual on how to use an ATMEL fingerprint board. 

[COLOR="Lime"]Question 1:[/COLOR]
In the manual it says that I should start the NFS server and for that, I should add the following line in the etc/exports file:

In my home directory (bulletproof is my home direcoty name) I typed:

*cd /etc*

then I listed the files in etc directory by typing in the following command:

*ls*

I then noticed that the exports file did not exist but stiil i decided to type the following and it gave an error:

[I]bulletproof@Bulletproof:/$ cd /etc/exports
bash: cd: /etc/exports: No such file or directory
[/I]


so what do I do from here??????:confused: 
[COLOR="Lime"]Question 2:[/COLOR]
Also when I typed in *cd /etc/fstab* the following error was given:
*bash: cd: fstab: Not a directory*

[COLOR="Lime"]Question 3:[/COLOR]

Once I'm in the etc/exports file I supposed to type:
*[COLOR="Red"]/nfsshare *(rw,all_squash)[/COLOR]*

and then start the nfs server by typing:
*/etc/rc.d/init.d/nfs start*

What does the commmand in red do??

---

### Post by Johan! on 2006-09-16
[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)
[http://en.wikipedia.org/wiki/Network_File_System](http://en.wikipedia.org/wiki/Network_File_System)
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)
[http://www.tuxmachines.org/node/7641](http://www.tuxmachines.org/node/7641)

Try google :wink: 
You can find lots of how-to's to install NFS on Ubuntu, and they tell you exactly what to do.

---

