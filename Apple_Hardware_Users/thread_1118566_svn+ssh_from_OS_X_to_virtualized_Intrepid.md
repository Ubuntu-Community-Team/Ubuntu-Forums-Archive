---
title: "svn+ssh from OS X to virtualized Intrepid"
date: 2009-04-07
forum: Apple Hardware Users
---

### Post by stesosaso on 2009-04-07
Hi everybody,

My problem is as follow :

My configuration :

[LIST]
[*]Macbook Pro with Leopard on one partition and on other partitions, Intrepid, boot via rEFIt.
[*]The installed Intrepid is virtualized in Leopard via Vmware fusion 2.0.2 and VMware tools are installed.
[/LIST]
 Intrepid has LAMP installed, openssh, samba as well as subversion.
I created a svn folder as fllowing : 

[LIST]
[*]/home/svn
[*]owner root:root
[/LIST]
The project folder, under svn, is spip206 and owner is root, group is spip206 with read write rights and I am part of that group (ie. /home/svn/spip206) 
source of that is : [http://www.think-underground.com/post/2008/04/13/Creer-un-depot-SVN-avec-acces-SVNSSH](http://www.think-underground.com/post/2008/04/13/Creer-un-depot-SVN-avec-acces-SVNSSH)

In a terminal (in ubuntu) I can acces, without any problem, my repository with :
```
svn list file:///home/svn/spip206
```Once I'll try to accès it via OS X terminal with :
```
svn list svn+ssh://local.ibat.fr/spip206
```(I have rooted localhost to local.ibat.fr on both systems : OS X and Ubuntu)
The system ask's me for my password and then return the following message :
```
svn: Authorization failed
```But when I have a look at auth.log in ubuntu I get following message :
```
Apr  7 09:17:30 ska23-ubuntu sshd[7945]: Accepted password for ska23 from 172.16.122.1 port 49161 ssh2
Apr  7 09:17:30 ska23-ubuntu sshd[7945]: pam_unix(sshd:session): session opened for user ska23 by (uid=0)
Apr  7 09:17:30 ska23-ubuntu sshd[7945]: pam_unix(sshd:session): session closed for user ska23
```My sources to build svn repository, ssh, etc are :

[LIST]
[*][http://www.think-underground.com/tag/Subversion](http://www.think-underground.com/tag/Subversion)
[*][http://svnbook.red-bean.com/en/1.0/ch06s05.html](http://svnbook.red-bean.com/en/1.0/ch06s05.html)
[*][http://svnbook.red-bean.com/en/1.0/ch01s07.html](http://svnbook.red-bean.com/en/1.0/ch01s07.html)
[*][http://chestofbooks.com/computers/revision-control/subversion-svn/Managing-Repository-UUIDs-Reposadmin-Maint-Uuids.html](http://chestofbooks.com/computers/revision-control/subversion-svn/Managing-Repository-UUIDs-Reposadmin-Maint-Uuids.html)
[*][http://www.huanix.com/2007/09/30/svnserveconf12-option-expected-svnserveconf/](http://www.huanix.com/2007/09/30/svnserveconf12-option-expected-svnserveconf/)
[/LIST]
For all groups (www-data for Apache, spip206 for svn, local ubuntu user) the same username and password is userd

If somebody has an idea what I schould do or where I schould digg to resolve my problem it would be a great help.

If you might need any other information please let me know.

I am not a linux specialist, I google a lot, and copy/paste while learning the commands. The same is valid for OS X.
And please forgive my english, as it is not my mother language...

Thanks in advance for your help and advise.

---

### Post by cyberdork33 on 2009-04-07
I believe this may be a config error in your server which means this is really not the best place. Can you ssh in? If that works, this is not a Mac or VM issue...

---

### Post by stesosaso on 2009-04-07
> **cyberdork33 said:**
> I believe this may be a config error in your server which means this is really not the best place. Can you ssh in? If that works, this is not a Mac or VM issue...

You are right, the problem came form the rights given to the svn project folder.
I followed the instructions given on this page :

[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

especially this instruction :

```
sudo chmod -R g+rws myproject
```and everything worked like a charm.

I have now a Apache server version controlled and virtualized to which I can connect form OS X (like my production server hosted in Paris) and all that locally on my MacBook Pro 3,1

Hope this can help those looking for such a local solution.
Thanks to all of you

Problem solved

---

