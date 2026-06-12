---
title: "Shareing a filesystem / directory with windows computers?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by ed_d on 2005-11-16
I have a filesystem (/multimedia) that I want to share with teh Windows users on our network. What would be the best way to set this up so they all have read and write access to this? It contains ISO images, and want to be able for them to put our burn from it. Thanks.

---

### Post by lutrafobic on 2005-11-16
One way to do this:

#1 Install samba from the "Synaptic package manger"

#2 then "System -> Administration -> Shared Folders"
There you can "Add" the folder(s) you want shared.

---

### Post by lutrafobic on 2005-11-16
Another way to do this:

#1 Install samba from your "Synaptic package manager"

#2 Open a terminal
#3 sudo nano /etc/samba/smb.conf
(opens the samba-configuration file)

An example of a configuration that will give ALL users read & write access to the folder /multimeda would be:


[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = MSHOME
security = SHARE

[SHARE]
path=/multimeda
read only = no
guest ok = yes 




Then press CTRL-X to exit, when asked to save press "Y" and then enter when prompted about filename.

Now to make the changes take effect restart samba with the command:
sudo /etc/init.d/samba restart

and you should change the write/read privlegies to that folder by running the command:
sudo chmod 777 /multimeda

OBS!!! you should ONLY do this if this machine is INSIDE a firewall/router, otherwise people from the internet can save stuff on that folder too... and you don't want that. :D


That should to it.

Chears.

---

### Post by ed_d on 2005-11-16
Cool, I can give that a whirl. I did already install samba, and was looking at the FAQ. The way described should be good though. I am within a firewall here too, so no worries on the outbound side.

---

### Post by dbott67 on 2005-11-16
Setup SAMBA on your Linux box and then go to SYSTEM -> ADMINISTRATION -> SHARED FOLDERS and setup an SMB share.

-Dave

EDIT: I got sidetracked for about an hour and forgot to hit post... it looks like I've been beaten to the punch... about 4 times! :)

---

### Post by Taurus548 on 2006-04-14
I am having difficult with my other members of the work group seeing the files on my new Ubuntu machine.
They find the machine but ask for a password. as I haven't set a password I don't know what to  enter.
Its like file shareing is not set up on this machine. I have gone thru the SYSTEM -> ADMINISTRATION -> SHARED FOLDERS but it does not help.

---

### Post by djsroknrol on 2006-04-15
Hi..

Make sure that Security is set to "Share" in your smb.conf file...

```
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = share

```

---

### Post by Taurus548 on 2006-04-15
"security=share"
is set, but it doesn't help. The machines on the network can find the box, and it will display the shared folders but when I try to open them the dialogue box says you do not have permission to access this resource.
Also the Ubuntu box can see and use all the resources available on other network boxes.

---

### Post by user1397 on 2006-04-15
I can't get samba to work either.
I did what lutrafobic said, and then went and looked on my wireless laptop to see if there were any signs of my computer showing up and there were none.  I don't even know where to look on a windows box.  Is it my network places, or c drive or shared folders or what? Also, in the samba shared folder that I have, under the windows settings, there is no host name.  Do I need one? What should it be?
Sorry for all the questions and thanks in advance.

---

### Post by user1397 on 2006-04-15
is anyone out there...............:(

---

### Post by antipattern on 2006-06-22
hmmm... I don't know much about samba itself, but i could try to help you with windos. It is supposed to be in Network Places, but it doesn't show up all the time.

First... check whether both computers are in the same work group. Go to "my computer" (i don't know the exact name, but the View that lists all your hard drives etc) open it. right click, and chose propperties (you can right-click on the My Computer symbol as well). Then, chose "Computer Name" (Second line, second from the left) and check what it says at "work group" and compare it to what it says in the samba.conf:
# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = MSHOME

(as lutrafobic pointed out, MSHOME is standard, but it might be sth else, eg. if you have a different language version of windows or configured it differently) 

I must be the same for both systems, doesn't matter which one you change. If you change it on the windows box, don't forget to restart it.

Well... If it is already the same or you already took it into account... i don't know. Sometimes windows plays weird and doesn't show all computers. In network places, chose "Show Work Group Computers" (again, i don't have the original English phrase, but it is sth like that. Should be in the left menu of the explorer at "Network tasks". If nothing shows up there, try to do a windows search, searching the name of your linux box in "computers and People"

So this is all i know right now... I'm not sure whether that helps, but well...

---

### Post by antipattern on 2006-06-22
Hmmm... I found this thread in a German forum as well, but I can't really make sense of it:
[http://www.heise.de/newsticker/foren/go.shtml?read=1&msg_id=10653504&forum_id=99536](http://www.heise.de/newsticker/foren/go.shtml?read=1&msg_id=10653504&forum_id=99536)
It gives a solution:
security = share
(...)
public = yes
read only = no
browseable = yes
create mask = 0777
However, this approach is described as Quick and dirty and the follow up post by a different user say it is potentually insecure. Therefore, use it only in a protected network. 

If you try to solve it this way, and you don't need read access, change no to yes.

Well, another User mentions a tool called Webmin and also talks about Samba users and groups. It appears to be related to Taurus' problem. But I don't know enough to make sense of it. Does anybody else know more about it?

---

