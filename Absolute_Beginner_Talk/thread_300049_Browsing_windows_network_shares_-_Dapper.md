---
title: "Browsing windows network shares - Dapper"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Shootfast on 2006-11-15
I'm relatively new to linux, and have through trial and error, learned quite alot over the past few days. However the only thing stumping me at the moment is opening my windows workgroup on the network.

I've set up samba, smbfs, and can see my network through smbtree. 

To try to browse them, I've currently been clicking:

Places>>>Network Servers>>>Windows Network>>>My_workgroup_name and then I see my computers. however, upon clicking them to browse, I am greeted by a message saying:

[I]"The filename "COMPUTERNAME" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."[/I]

I have tried right clicking and choosing "Connect to this server" which I assume links it to my desktop, for there is now a new icon, and if i select "Open with File Browser" I get one step further however...
[I]
"The folder contents could not be displayed.
Sorry, couldn't display all the contents of "COMPUTERNAME"."
[/I]
I am able to access my ubuntu computer from windows through the share folder I created at /media/samba , although i'd kinda like 2 way traffic :???: 

I have tried to find threads already covering this issue to no avail. The windows peer-to-peer thread fixed things from the windows end.

Any advice?

---

### Post by lofgren on 2006-11-15
Heya,
I've tried a few flavours and each is a bit different - particularly between kde and gnome.  Looks like you are using ubuntu and gnome.

Best bet long term is probably to look at putting permenant mappings into /etc/fstab if you plan to be browsing across the network a lot. That way it will be there as soon as you boot up, with a path you can use for all apps.
There are possible issues with security and I have also read about corrupting windows data.. I recommend reading into it further.

Without going into fstab and making mappings permenant, I have personally used the "connect to computer.." option since installing recently.

So, instructions are..
Places -> home folder
File -> Connect to server
Select Windows share (I believe you've gotten this far!)
Server = your remote machine
Share = the windows share. maybe d$ or perhaps you share out specific directories
folder - doesn't seem to be needed. not sure what it is, perhaps you can specify sub-paths of the remote machine
username - duh.
domain name = the remote machine name if you are in a workgroup
name to use for connection - this is what appears under the link/icon on the desktop and within your file browsing in applications that use nautilus.

Hope that helps ;)

PS> I dig your avatar!

---

