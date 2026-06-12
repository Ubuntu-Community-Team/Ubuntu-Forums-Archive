---
title: "Ubuntu's worm in the bud"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Roger D on 2007-03-27
Hello

I love using Ubuntu - the Gnome GUI is simple and intuitive, the filing system is clean and elegant, I don't have to worry about viruses and spybots, and I'm not contributing to the coffers of a company with an unhealthy near-monoploy on desktop operating systems. That said, I sometimes wish that the approach to in-built help and documentation was a little more, well, conventional.

Take my current problem. I've two PCs, host names roger-old and roger-new, both on the same wireless LAN.  Currently, I'm using a USB stick to transfer files from roger-old to roger-new. It's crude, but it works. However, what I'd really like to be able to do is to 'see' my home folder on roger-old from roger-new. My Microsoft-using friends tell me this is no big deal, and, indeed, under System>Administration>Shared Foders, there appears to be a utiliity designed expressly for this purpose.

I open up Shared Folders on both machines, install NFS, and add the local home folders. However, I've no idea what to do next. I click on help, but it appears no help is currently available. I've also looked under Places, hoping to see the added home folders, but without any joy.

Naturally, I've done a lot of searching on the web and in various forums, but this has been an unproductive and somewhat discouraging experience. I couldn't  find anything explaining how to use Shared Folders, however, I found a wealth of complex postings on the problems of communicating between different machines on a common LAN. Overwhelmingly, these were related to getting Windows and LInux machines interworking, where the preferred communications protocol is, it seems, samba.

I'm not decrying all the amazing, cooperative effort that these postings represent, I've had some really wonderful help from the Beginners Forum in the past, it's just that it doesn't seem a terribly efficient way of addressing a common problem. Shared Folders appears to have been designed as a simple GUI-base approach to my problem, and similar problems described in various postings, and yet all the posting describe solutions based on comand line entries. Many of these are offered without explanation, which, to the uninitiated, makes the whole thing akin to magic. You can make it work; it's just a case of invoking the right spell. I'm very happy to use the command line, but it seems dangerous to be entering commands into your PC, in sudo mode, when you don't understand what you're doing.

So, what's wrong with Shared Folders? It presumably works, and somebody, somewhere, must know how it works, or else what is it doing being included as a basic element in a long-term support distribution (6.06)?

I accept that an operating system is a large, complex, evolving entity, and there are bound to be  some rough edges, but surely these rough edges shouldn't extend to elements, like Shared Folders, included as part of a initial installation? As a grateful Ubuntu user, I'm happy to do my bit to rectify this situtation. If I could solve my own problem I'd happily write a HOW TO. But I can't, so I'm in a bit of a Catch 22 situation there. Alternatively, is there some way of bringing attention to the lack of help and documentation support for Shared Folders - other  than by  this posting? I've had a good look around the Ubuntu web site, but I can't see and obvious link to the 'powers that be'.

All suggestions and comments, much appreciated.


Roger D

---

### Post by eljalill on 2007-03-27
The easieat way I know of, is to connect via ftp.
You have to have vsftpd I think, 
with that you can "share" your home directory when you open
system>administratin>services and then tick the vsftpd box. 
Do that on both computers, and you should find the other computer in "Network" .

But for singel files I just use the command line and ftp...

PS: I think what you are looking for are things like ftp and ssh... I found loads of stuff when I searched the forums for any of these and "GUI"

---

### Post by halitech on 2007-03-27
so you do have the folders shared on both systems? do you have the same user set up on both systems? I have a network setup with a windows box and 2 ubuntu boxes and after sharing the folders, adding the users, I went to 

Places - connect to server

then select service type as windows share, put in the IP address, folder name you want to connect to and the username and password. Once completed, you should have it show up on the desktop.

---

### Post by clparker on 2007-03-27
I agree, more should be done about the documentation. I've had nothing but trouble finding help w/ connecting the two PCs i use @ home. One's running Dapper, and the other's XP Pro SP2. The Ubuntu Box sees the PC files, but I've NEVER been able to get XP to see the ubuntu box. (shrugs) I just blame Microsoft...

---

### Post by Roger D on 2007-03-27
Thanks for the response

What do you mean by 'sharing the folders, adding users'?

Roger D

---

### Post by dstew on 2007-03-27
I tend to agree with you, Roger. I struggled quite a bit with sharing. The most bizarre problem I had was mounting a samba share from a network over VPN. The share would mount, but I could not see any files. Finally, by experimenting, I found out that the problem was that one file in the share had a "trademark" character in its filename, that samba was not recognizing. That made the whole directory fail to list.

What really helped me to get sharing working was using the samba client program **smbclient** on the command line. It works like ftp, but with samba.

---

### Post by Tulx on 2007-03-27
> **clparker said:**
> I agree, more should be done about the documentation. I've had nothing but trouble finding help w/ connecting the two PCs i use @ home. One's running Dapper, and the other's XP Pro SP2. The Ubuntu Box sees the PC files, but I've NEVER been able to get XP to see the ubuntu box. (shrugs) I just blame Microsoft...

Well, you can make win 98 and 2k seeing Ubuntu (for me it requrired two sleeples nights but I got them working :) ) I think that XP SHOULD handle that too but i dont have any experience about that. Suprisingly win 98 even works together with ubuntu than 2k.

---

### Post by Woody@N87 on 2007-04-04
Although all the answers will do the job, on 6.10 it seems a little simpler to me.  I have four  XP pro machines and one ubuntu.  The XP's have a couple shared folders that are wide open (shared without a password)   

If I go to Places->Network Servers a file  browser opens up and shows an icon called Windows Network, double click that and I see the Name I gave the router, double click that and I see all the computers.  Double click the desired computer and I get the shared folders/files.  I can open an word doc and edit it directly off of the windows disk just fine.   I just did this as I typed this reply to confirm.  If Samba is running it's not because of anything I did.  After this you can go back and set your passwords if you like.

The moral of that long boring story was it might be better and easier just to move up to the 6.10 version or maybe the next version due out shortly.

---

