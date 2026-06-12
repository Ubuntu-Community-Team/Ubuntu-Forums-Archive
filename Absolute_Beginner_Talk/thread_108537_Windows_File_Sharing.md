---
title: "Windows File Sharing"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Freddie on 2005-12-26
Today I wanted to transfer some files between my ubuntu computer and my iBook (OS X). Rather than use ftp or something like that I decided to have a go at using shared folders, so I selected the directories that I wanted to share (/home)and set my samba settings (just giving it a name). Next, on my iBook, I went network and saw Mshome and when I selected it I saw macserv (the name of the ubuntu computer) I clicked on connect and then it crashed on me (finder). I know nothing about windows file sharing, how to set it up or anything like that (even when I had two windows pc's I did not try it). Can someone tell me what I need to do to be able to share a folder between these two computers. Now, while there is a windows computer connected to my router I am quite happy to use a *nix protocol, as long as it means that I can share a folder on my server.

---

### Post by ghosthere on 2005-12-26
Have you tried connecting to the computers with there IP addresses?
I connect my PC, MAC, and Linux computers with my dlink router asigning DHCP names on the router settings. and connect with there IP's. If it only connects when the pc is on the pc is prob-ly assigning DCHP to the MAC and PC... I Hope this helps

---

### Post by deNoobius on 2005-12-26
Freddie, I also had a devil of a time getting my Mac (OSX Tiger) to "see" my Ubuntu box.  I figured out one way, using ssh and the terminal command line on the Mac (I still don't have a solution for using the Finder, sorry).  Actually,  once I figured it out, it wasn't hard at all--I'm still in the learning process, tho!


-Install openssh on the Ubuntu machine (it's in the repositories).
-Find the IP address of the Ubuntu machine 
-If you're using Firestarter, open the ssh port (22) either to your whole network or to the Mac (by typing in the IP of the Mac in the appropriate box)
-On the Mac, open the terminal and type at the prompt:  
ssh -l username 192.168.*.* (where username is your Ubuntu user login name and the *.* is the actual IP of the Ubuntu box)

-when asked for a password, type the Ubuntu password.

You should be in.  You navigate on the remote machine just as if you were in the Linux command line.

Hope this helps!

---

### Post by Freddie on 2005-12-26
I currently SSH to it (and transfer files using sftp). However, my music collection (which is a good few gb) is all on my ubuntu computer, and I would like to be able to listen to it from my iBook and Gentoo Linux computer without having to copy it all across. So, I was thinking that windows file sharing might make this possible.

---

### Post by Estariel on 2005-12-26
I have no idea whether OSX installs smbclient as default. If it does, you can do the following:

Export the mp3 directory on your Ubuntu box.
Memorize Ubuntu Box's IP address.
On the OSX box, create a directory to which you want to mount the mp3 directory. Let's call it mp3osx.
Open a terminal on the OSX box.
Issue
```
smbmount //IPofUbuntubox/mp3 /path/to/mp3osx
```

If this does not return an error, you should have your mp3s mounted in mp3osx.
Maybe you must be root on the OSX box (I don't own OSX, I just hope this works since OSX is essentially unix...)

edit: you might want to try NFS since none of your computers are windows computers. So there is no reason to use the troublesome samba protocol

---

### Post by Freddie on 2005-12-26
Tell me more about this 'NFS'....
When I type in 'smbmount //192.168.0.5/music /home/freddie/Music' it asks me for a password, but I have no idea what it is (where do I set it?).

---

### Post by Estariel on 2005-12-26
edit your /etc/samba/smb.conf
under ##Authentication set 
change the line
```
;   security = user

```
to
```
security = share
```
(make sure to remove the semicolon)

This will disable most security features (password etc.)
I don't really know my way around samba's authentication system, I always set the security to "share"... - I know, that's the worst security practice possible, but I don't have anything in my shared directory I'd have to worry about.



NFS is the Network File System.
wikipedia has a nice article on it: [http://en.wikipedia.org/wiki/Network_File_System](http://en.wikipedia.org/wiki/Network_File_System)
If you follow the links below the article, it will lead to some nice howtows on how to set it up.
This is the unix way of easily sharing files between computers.
But I think it's security is really bad (compared to a correctly set up samba system)

---

