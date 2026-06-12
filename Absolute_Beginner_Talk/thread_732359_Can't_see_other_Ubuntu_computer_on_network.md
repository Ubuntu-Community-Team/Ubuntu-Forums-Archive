---
title: "Can't see other Ubuntu computer on network"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by reabralop on 2008-03-22
Hello, I've been searching half this day to figure out how to network my 7.10 and 6.10 machines together. I've found alot of info on networking computers but I still don't see the other computer on either machine in my wired network. I've done the "share folders" in the system admin and found the ip address for both machines. 
One post I found claims it's easy to share files between Ubuntu machines but I still haven't figured out how to do it. I don't see the computers! I don't see a clear explanation on how to set this up.
Can someone please help me! Thank you.

---

### Post by tvtech on 2008-03-22
OK here is the deal it is NOT easy to network two ubuntu computers together to share files.
This is because no native file sharing system is installed by default 

in order to network them you will have to install samba or nfs or both then you can use the share folder tab in administration to set up share folders.  
you may need to enable a password on them as well 

in samba this is done by
 
username@localhost:~$sudo smbpasswd -a username
please note that this should be your user name once this is done you should have simple authentication and access to the shares!
either install smb, or nfs or both!  

username@localhost:~$sudo apt-get install samba

---

### Post by reabralop on 2008-03-22
When I open the shared folders from the system-admin, it shows the folder I selected as "shared through Unix networks (NFS)". That means it's installed, right? What do I do after that?

---

### Post by tvtech on 2008-03-22
that should mean it's installed. I'm not sure what it shows up as default I've always installed samba and mine only show's up as smb shares since I haven't installed nfs  at this point in samba you have to install both the samba client and the samba server but just installing samba alone will do that. 

with nfs you'll have to install nfs-server  and nfs-client 

pop into a terminal and type sudo apt-get install nfs-server nfs-client  if you'd like to use nfs.   

then you should be able to use the share folder dialog in the admin to set up shares and the computer should see them when you go to 
places>network  I don't know if you need to do any authentication with nfs

**gimme a few minutes and I"ll install nfs and see what it brings up!**

I always use samba cause it was easier to set up my file server with that because my wife doesn't want to switch away from windows

okay this looks pretty standard in the gui.  this should be easy.  once you have NFS installed on both computers go to 

System>administration>sharedFolders

once inside select nfs then when you allow your host add the computer name  so the localhost part of username@localhost:~$  once you enable each of the other computers as hosts you should be able to easily share files from one box to the other!

let me know how it goes

---

### Post by Neo0351 on 2008-03-22
Here's how I get samba working on my computers.  [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

---

### Post by Krydahl on 2008-03-22
I got this to work a while back, but I'm not using it anymore and can't remember the details.

As far as I recall, having set up a folder as shared on the server pc, I had to mount it on the client.

I can't recall if there were any special options.

---

### Post by reabralop on 2008-03-22
Is there an advantage to using smb vs nfs? I was under the impression that you only use smb if you are trying to network with windows machines. I'm gathering now that you can use either with a linux only network?

---

### Post by tvtech on 2008-03-22
there are a number of security issues with both.  supposedly smb is more secure.  I don't know that there is an advantage either way.

---

