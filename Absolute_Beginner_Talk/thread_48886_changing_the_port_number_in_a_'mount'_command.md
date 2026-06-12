---
title: "changing the port number in a 'mount' command"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by mikeb on 2005-07-14
I am trying to mount a volume on my OS X machine on Ubuntu. Following instructions in the unofficial guide, I've installed everything and configured everything (I think). When using the command recommended in the guide (sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword), I discovered that Ubuntu is trying to connect to port 445, but the OS X firewall is configured to use ports 548 and 427 for file sharing.

So, when I issue the command without port number, I get an error report referring to port 445. When I modify the command so: 'sudo mount //192.168.0.1:548/linux /media/sharename/ -o username=myusername,password=mypassword', I then get a different error saying 'can't find address for //192.168.0.1'

I've searched the Internet for a solution, and what I found was I could add a port=n argument. I've now tried 'sudo mount //192.168.0.1:548/linux /media/sharename/ -o port=548 username=myusername,password=mypassword' but it still doesn't work.

How can I fix this? Thanks.

---

### Post by dave9191 on 2005-07-14
Have you tried 

sudo mount //192.168.0.1/linux /media/sharename/ -o port=548 username=myusername,password=mypassword

Just using the port=548 rather then also having 192.168.0.1:584
Dave

---

### Post by mikeb on 2005-07-14
[QUOTE=dave9191]Have you tried 

sudo mount //192.168.0.1/linux /media/sharename/ -o port=548 username=myusername,password=mypassword

Just using the port=548 rather then also having 192.168.0.1:584
Dave[/QUOTE]
 Whoops, my mistake. Yes, I did it the way you suggested -- without the :548--  but did not edit my message correctly. I will try it again and post the result here.

Thanks.

---

### Post by mikeb on 2005-07-14
[QUOTE=mikeb]Whoops, my mistake. Yes, I did it the way you suggested -- without the :548--  but did not edit my message correctly. I will try it again and post the result here.

Thanks.[/QUOTE]
 I believe this version of 'mount' does not seem to support the 'port=n' argument. When I try it, I get a list of supported usage and when I look at the man file for 'mount', it does not seem to list port=n as a valid use. Uh oh.

---

### Post by dave9191 on 2005-07-14
Only thing in the man pages about using mount with port=n i found is 

Mount options for nfs
       Instead  of  a textual option string, parsed by the kernel, the nfs file
       system expects a binary argument of  type  struct  nfs_mount_data.   The
       program   mount   itself  parses  the  following  options  of  the  form
       ‘tag=value’, and puts them in the structure mentioned: rsize=n, wsize=n,
       timeo=n,  retrans=n,  acregmin=n,  acregmax=n,  acdirmin=n,  acdirmax=n,
       actimeo=n, retry=n, **port=n,  mountport=n**,  mounthost=name,  mountprog=n,
       mountvers=n,  nfsprog=n,  nfsvers=n,  namlen=n.   The  option  addr=n is
       accepted but ignored.  Also the following Boolean options, possibly pre&#8208;
       ceded  by  no  are recognized: bg, fg, soft, hard, intr, posix, cto, ac,
       tcp, udp, lock.  For details, see nfs(5).

---

### Post by mikeb on 2005-07-14
It is weird because issuing the command results in a list of accepted uses, which would seem to mean that the argument is not accepted.

If I edit the /etc/fstab file to include the disk I want to mount, would that work? Is that where mount looks for mountable volumes? If not, is there another file that I could edit?

Thanks.

---

### Post by dave9191 on 2005-07-14
I don't really know, Im not an expert on the mount command. But why dont you allow OS X to use port 445 for file sharing? Im sure that there is a way to tell mount what port to use tho. 

Dave

---

### Post by mikeb on 2005-07-14
Well, I finally found the solution: in the OS X firewall preference there is no port for SMB, however, by selecting 'new' SMB is one of the choices and it is already configured to use port 445. So, I've done it and it works!

However, I now have another problem: I made symbolic links on the Mac to directories I wanted the Linux machine to have access to. While the OS X terminal can follow the links and see the directories, the Linux machine cannot. There seems to be no permissions problem, so I am not sure exactly what the problem is. When I look at the directories in Linux, it shows the path as '/directory/'. Could that be the problem?

---

### Post by dave9191 on 2005-07-14
if you do 'ls -l' what do the sym links look like to linux ? 

Dave

---

### Post by mikeb on 2005-07-15
[QUOTE=dave9191]if you do 'ls -l' what do the sym links look like to linux ? 

Dave[/QUOTE]
 Linux calls them broken links and ls -l shows something like this: file -> /directory/sub

In this example, 'sub' is also a directory, but lacks the trailing slash. Could this be the problem? When I make them in OS X, I use ln -s /target destination. If I put a slash after 'target' in this example, the operation fails with an error.

Mike

---

### Post by dave9191 on 2005-07-15
I dont know if the trailing / would make a diffrence. But since linux calls the broken links, maybe it doesnt have the permissions to go to them. The folders that the links point to, and every parent folder must have proper permissions. 

On the Mac you are logged in as a user who has permissions to everywhere. But when you mount the network storage on the linux machine, you arent a user who has access to the whole mac machine, just the folders / files in the network storage area. So when you have links to somewhere else on the hdd, then you cant see them. Give read permission to the others group in the folder that the link points to and try it. If not, you'll have to give read permissions to each parent folder along the way. Well thats my guess. 

Dave

---

### Post by mikeb on 2005-07-15
[QUOTE=dave9191]I dont know if the trailing / would make a diffrence. But since linux calls the broken links, maybe it doesnt have the permissions to go to them. The folders that the links point to, and every parent folder must have proper permissions. 

On the Mac you are logged in as a user who has permissions to everywhere. But when you mount the network storage on the linux machine, you arent a user who has access to the whole mac machine, just the folders / files in the network storage area. So when you have links to somewhere else on the hdd, then you cant see them. Give read permission to the others group in the folder that the link points to and try it. If not, you'll have to give read permissions to each parent folder along the way. Well thats my guess. 

Dave[/QUOTE]
 I looked at all folders and parent folders and all of them seem to be universally readable. One thing I found a little weird is that when I asked for the Properties of the links in Ubuntu it described the MIME type as: application/octet-stream

It doesn't make much sense to me, but a symbolic link is an application?

---

### Post by dave9191 on 2005-07-15
I dont think that they should be read as an application. I dont know what else to suggest. Maybe someone else has some ideas about this. 

Dave

---

