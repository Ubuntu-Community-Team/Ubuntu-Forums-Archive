---
title: "Accessing Windows Shares"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by Joshua on 2005-08-26
Well, I wanted to do two things, read and write files on my Windows 2000 Pro box from my Ubuntu Hoary box, and vice versa.

I did:

sudo aptitude install samba
sudo aptitude install smbfs  (not sure what this is actually for)

Then I followed the Unofficial guide and edited the smb.conf file and added users and stuff.

But now I can only read and write files on the Ubuntu box FROM the Windows box.

When I try to connect to the Windows box from Ubuntu (either with the network or connect to servers menu items) a window pops up asking me for a user, domain, and password.  I've tried all the combos I can think of (I assume they should be for accounts that are already on the Windows box), but most of the time it will accept the combination I choose and open a window that says it's my Windows box, but there is nothing in it.  And I do have a shared file on my Windows box (I can see it in the network neighborhood on the Windows box).

Only thing I can think is that maybe there is something wrong with the users or permissions on my Windows box.  I just use the Administrator login for everything (no normal user) and the permissions on the shared folder say that the group "Everyone" has all permissions.  When I log in from Ubuntu with Administrator and <adminpass> it won't work.  So I created a new user on the Windows box and added the user to the permissions for the shared folder, but still, it doesn't work.  Can anyone help?

---

### Post by KingBahamut on 2005-08-26
User permissions issue. 

At the command line you can use smbclient to determine the shares available. I find this tool invaluable and not replaceable by any other. 

Are you being controlled by a domain or is this your home network?

---

### Post by void_false on 2005-08-26
I have almost the same problem exept it is inverted. I can with no problem access wins' shares from Ubuntu. But when using Windoze, I can only see Ubuntu box in Network Places. If I try to access Ubuntu's shares from Win, it says computer is unreachable.  :???:  :neutral:

---

### Post by KingBahamut on 2005-08-26
void, and you have your accounts set with smbpasswd proper and the users are all proper?

---

### Post by Joshua on 2005-08-26
Well I'm not at home right now so I can't try out the smbclient command yet, but it is a home network.  I set it up with a workgroup name.  So when I open the Windows Network icon, it shows another Icon with my workgroup name.  Then when I open that it has both computers in it.

Now that I think about it, maybe I have some settings messed up.  In Windows it always says Workgroup/Domain when it asks.  But in Ubuntu sometimes it seems like they are different things.  That window that pops up when I try to log in from Ubuntu always asks for "Domain" but sometimes I put in my workgroup name there.

There are two other places where I've done that, too (if I remember correctly).  In the setup menu for the network connections in Ubuntu (the one where you set up your ethernet card or modem) - somewhere in that it asks for a domain and I put my workgroup there.  Then, also if you click the shared files menu and click something like general windows settings.  I put my workgroup in the domain there, too.  Maybe that doesn't have anything to do with it.  But the reason I thought about it is that the Windows Networks icon still has both my workgroup that I set in Ubuntu and the Windows box, as well as the default MSHOME that was set in Ubuntu before.

So if I try smbclient from the command line, what will that tell me?  If it's a permissions problem, is there anything else I need to set up in Windows to get it to work?

---

### Post by KingBahamut on 2005-08-26
smbclient is a client that can 'talk' to an SMB/CIFS server. It offers an interface similar to that of the ftp program. Operations include things like getting files from the server to the local machine, putting files from the local machine to the server, retrieving directory information from the server and so on.

See link -- [http://www.samba.org/samba/docs/man/smbclient.1.html](http://www.samba.org/samba/docs/man/smbclient.1.html)

---

### Post by Joshua on 2005-08-26
[QUOTE=KingBahamut]void, and you have your accounts set with smbpasswd proper and the users are all proper?[/QUOTE]
 King, in your response to void, what do you mean be "proper."  I do know that it took me a while to figure it out, but I couldn't just use the "Shared Folders" menu in Ubuntu to get it to work.  I had to actually use the command line and this section of the Unofficial Guide:

[http://www.ubuntuguide.org/#addeditdeletenetworkusers](http://www.ubuntuguide.org/#addeditdeletenetworkusers)

Then, I had the same use and password set up on both systems so I replaced "system_username" and "network user" with that user and password.  I think that "system_username" is supposed to be a user that is on the Ubuntu box, and "network user" is supposed to be a user on the Windows box but I'm not sure.

---

### Post by Joshua on 2005-08-26
[QUOTE=KingBahamut]smbclient is a client that can 'talk' to an SMB/CIFS server. It offers an interface similar to that of the ftp program. Operations include things like getting files from the server to the local machine, putting files from the local machine to the server, retrieving directory information from the server and so on.

See link -- [http://www.samba.org/samba/docs/man/smbclient.1.html](http://www.samba.org/samba/docs/man/smbclient.1.html)[/QUOTE]
 So you're saying that I need to use smbclient to access the Windows computer, instead of trying to use the menu items?  Or am I supposed to use smbclient to figure out what the username and password should be?

---

### Post by KingBahamut on 2005-08-26
You can use smbclient to access or move the files, you can use smbclient to see the shares on the system, and you can use smbclient to determine the shares that can be seen by the system and with proper account verification, access them.

---

### Post by void_false on 2005-08-26
Well, it's getting a bit complicated. Is there anyway I can make access without username and password? Hell, its home network, and I believe everyone here.  ;-)

---

### Post by Joshua on 2005-08-26
[QUOTE=KingBahamut]You can use smbclient to access or move the files, you can use smbclient to see the shares on the system, and you can use smbclient to determine the shares that can be seen by the system and with proper account verification, access them.[/QUOTE]
 Ok, I'll try that out when I get home.  Thanks.

But, that's all going to be on the command line, right?  I thought Ubuntu would be easier than that...

---

### Post by Joshua on 2005-08-27
Ok, I got everything to work.  But there is one quirk that I'm hoping someone can clarify.

It appears that the network browser that you get when you click on "Network Servers" will not show files with names longer than 12 characters.  If you right-click on a server and choose "Browse Folder" and then type the shared folder in the location bar, you can still look in the folder.  It just doesn't load all the shared folders automatically.  Is this a bug or is there a reason that the file browser won't automatically show shares that have names of more than 12 characters?

---

