---
title: "Samba config"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Lymen on 2006-06-12
[COLOR="Black"]Hello!
I'm new to unbuntu and am trying to get it to network with my XP's in the house, but I can't seem to access the samba smb.conf in order to change the work group.  I am logged in as root and here is the output from my terminal:[COLOR="Red"]root@buggjohnson:/home/user# /etc/samba/smb.conf
bash: /etc/samba/smb.conf: Permission denied
[/COLOR][/COLOR]any help would be greatly appreciated.
thanks!

---

### Post by Nikusan on 2006-06-12
[QUOTE=Lymen][COLOR="Black"]Hello!
I'm new to unbuntu and am trying to get it to network with my XP's in the house, but I can't seem to access the samba smb.conf in order to change the work group.  I am logged in as root and here is the output from my terminal:[COLOR="Red"]root@buggjohnson:/home/user# /etc/samba/smb.conf
bash: /etc/samba/smb.conf: Permission denied
[/COLOR][/COLOR]any help would be greatly appreciated.
thanks![/QUOTE]

try gedit /etc/samba/smb.conf

---

### Post by RudolfMDLT on 2006-06-12
Hi!

To set up a XP Ubuntu Network you don't meed to touch the config file. And you don't need to be logged in as root. Any mistakes you make can turn out to be quit distructive. System => Administration => Shared Folders. Click properties and then click the windows settings. There you change the workgroup.

EDIT:

Here's a copy out of a previouse post i made on samba networking, it might help later:
> 

First - make sure all the PC's are on the same workgroup - Change it to HOMENET or NEARYNET or
any other clever name you can think of.

Then share files on all the PC's. In windows, don't use the wizard - just enable file sharing.

Then you have to add users to the Ubuntu machine so that the windows PC's can access it.
First you have to add users to the Unbuntu PC user list:
SYSTEM=>ADMINISTRATION=>USERS AND GROUPS.

Here you add, for example "kitchenpc" and set the password.

Then you add kitchenpc to the Samba user list:
This is done in the terminal:

1) sudo smbpasswd -e yourname (you're user name)
2)Type and retype new Samba password
3)sudo smbpasswd -a XP username (kitchenpc)
(the usernames of your network users)
4)Type and retype their passwords

You have to redo step 1 and 2 every terminal session - so first add all the users to the users and groups list and then do the Terminal part where you only have to repeat steps 3 and 4 for every user added.

Now when the login pops up from the XP side you can just login and everything should work fine!

For more, see this how to:

[http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)

Cheers!

---

### Post by Lymen on 2006-06-12
Thanks for the quick response, you guys kick ***!
my problem persists... I switched my workgroup, but I still cant get into my two XP machines.  I see them in my network server folder but get an error when I try to open them.  

(I tried the gedit command but got a read only response.)

thanks for your patience with the nubie!

---

### Post by RudolfMDLT on 2006-06-12
[QUOTE=Lymen]
(I tried the gedit command but got a read only response.)

[/QUOTE]
If you get a read only using root,thats weird, so try re-installing samba. This sounds like Windows advice, I know. Go to synaptic, search samba, uninstall it and redownload it. It's not that big. But not being able to open a file with root is not something I have heard of yet, though I've only been using Ubuntu for a month or so.

EDIT: Forgot about something. Most XP machines won't even allow other XP machines to view there shared contents if it isn't shared correctly! I want you to create a new share in XP, any folder. Share it like this; Right Click on the folder => Click on the sharing tab. There you select the option that says just enable sharing and allow users to change your files, do not use the wizzard to share files. Hope that helps!

---

### Post by Nikusan on 2006-06-12
[QUOTE=Lymen]Thanks for the quick response, you guys kick ***!
my problem persists... I switched my workgroup, but I still cant get into my two XP machines.  I see them in my network server folder but get an error when I try to open them.  

(I tried the gedit command but got a read only response.)

thanks for your patience with the nubie![/QUOTE]

I assumed you'd still be root. Try sudo gedit instead.

---

### Post by Iowan on 2006-06-12
There's a thread around here somewhere on remounting XP shares.  Ubuntu can read XP shares, but writing them is a li'l trickier.

---

### Post by Lymen on 2006-06-13
I finaly got em networked!:D 
It seems I did not have all of samba loaded and running...I found the rest of Samba in synaptic then connected to each individual computer through "connect to server" with their specfic IP.  Now I have each XP available on my desktop!

Lots of cool stuff in Add/remove too!  this may take a while to get used to but linux is exciting!  I'm shure I'll be back with more questions.;) 
thanks again for all your help!
greatly appreciated.

---

### Post by Nikusan on 2006-06-13
Congratulations for sticking with it! You'll have fun I'm sure. :D

---

