---
title: "Sharing  a folder from a windows machine"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Yellowdog428 on 2007-11-26
OK I have access to he windows machine.  I have not installed installed Samba but it seems Gusty picks up my windows network with no problem.

I can take files and save them to my laptop no problem but I need a program to be directed to a folder on the Windows machine.

Here is what I am trying to do.

My laptop is running Gusty.  I was looking for a way to stream to my airport express and to my supprise the current version of Wine will run ITunes and I can stream to my airport express!!!!! Only problem is I cannot browse to the Windows Machine to add all my music to the playlist.......

So I thought I could mount the folder on the Windows machine to my desktop of the Ubuntu laptop, but I cant figure out how.  Then I thought I could mount the harddrive, ut I cant figure it out.

Do I need to install Samba?  If so any good howtos out there?

Am I even thinking the right way or is there another way do it?

Thanks
Cheers

---

### Post by ofb on 2007-11-26
SMB is already installed, and that's what you're using to browse your Win network. 

If you want to mount a remote folder or drive, that's different. That's what NFS does.

Here's as good a start as any. Follow links.
[http://ubuntuforums.org/showthread.php?t=617132](http://ubuntuforums.org/showthread.php?t=617132)

A bit of a heads-up: try to stay with information for 7.10 or at worst 7.04. Ubuntu and associated applications like firewall GUIs keeps improving, so you don't have to do as much as you used to. Also keep your lights on anyways - often the information is written by 'old hands' who haven't looked for improvements, so are telling you the old way they knew. Or an old way they read elsewhere and are simply repeating.

SMB is pretty simple now. NFS isn't quite as simple, but much simpler than it was. Depending of course what you're doing with it - setting up for multiple users of a share across the internet takes more configuration than a simple share between one person's two machine's at home.

Backing up - I'm not sure why you can't browse the remote machine through SMB. That might be a Wine gotcha that you'll have to look into.

EDIT: I should say that I'm not sure you can do NFS with a Win source. Perhaps that's only a *nix option.

---

### Post by Yellowdog428 on 2007-11-26
Just to make sure we are on the same page.

I am trying to put a "shortcut" to the folder on the desktop (or anywhere else that the folder manager could find it) so I can add the folder to the playlist.

I am attaching a few pics so you can see what I am looking at.

---

### Post by Yellowdog428 on 2007-11-26
sorry for the double post.

I got the drive mounted, but I cant browse to it in itunes add file folder option.  

Any Ideas?  I figured I could see it if I mounted the folder to the desktop, but it is not in the browser....

Thanks in advance.
Cheers

---

### Post by Yellowdog428 on 2007-11-27
Well unfortunately this may be a deal breaker with the wife....

I think me needs to install windows back on my laptop...  
Thanks ofb for your help.

Cheers

---

