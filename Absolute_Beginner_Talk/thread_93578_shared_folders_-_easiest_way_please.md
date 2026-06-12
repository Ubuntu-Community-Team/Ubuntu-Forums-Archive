---
title: "shared folders - easiest way please"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2005-11-22
Hi there,

Simple newbie question: I would like to...

1. transfer files back and forth between two machines (one ubuntu, and one knoppmyth)
2. set up directories on each machine to be view as local directories - music files on ubuntu show up in knoppmyth for example.

Can I get some advice please on how to set this up - I have had a look around the forum but not found anything.

Many thanks in advance,

John

---

### Post by unixfudotnet on 2005-11-22
I am not sure what knoppmyth is, yet if it is a linux/unix, you may use nautilus or konq to browse the other machine via http, ftp, or ssh.

konq -> fish://username@server.name.net/
  * this will start an interactive ssh session
        
nautilus -> ssh://username@server.name.net/
  * this will start an interactive ssh session

You may use this method to drag and drop files around over secure channels.

If you wish to do this without both sides being linux/unix, you may setup Samba and mark directories/files as shared. There are several Samba howtos out there, and Ubuntu provides a Samba gui tool by default (I think). Then in linux you can smbmount (provided smbfs support is in the kernel) the share to your local filesystem and browse (nautilus and konq support this, as does firefox if you compile it in) or browse regularly in Windows as you would another Windows machine with shared folders.

---

### Post by pompeyjohn on 2005-11-22
hi there,

thanks for the response.

Knoppmyth is a debian based distro - you can check it out here 

[it rocks]("http://www.mysettopbox.tv/knoppmyth.html")

I am running Ubuntu, so nautilus it is...

I can ssh to it through the location bar, but I just tried to create a connection to it and add it as a 'place.' Something went wrong though and it doesnt connect. I guessed that the port would be 25, but not sure about that. Now I cant delete this incorrect place from the place list. How can I do that?

The reason I asked about all this is because I was wondering if there was a fstab type file for network shared folders.

cheers

---

### Post by ed_d on 2005-11-22
Install and set up Samba from [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

Then go to System>Administration>Shared folders. Add the folders you want to share and check them as browsable. All done.

---

### Post by pompeyjohn on 2005-11-22
OHYMGOD!!

I cant believe I didnt spot that! I must have looked at that menu a thousand times lol

thanks for pointing that one out!!

---

### Post by patrick295767 on 2005-11-22
[QUOTE=pompeyjohn]Hi there,

Simple newbie question: I would like to...

1. transfer files back and forth between two machines (one ubuntu, and one knoppmyth)
2. set up directories on each machine to be view as local directories - music files on ubuntu show up in knoppmyth for example.

Can I get some advice please on how to set this up - I have had a look around the forum but not found anything.

Many thanks in advance,

John[/QUOTE]

NFS file sharing (not NTFS);
----------------------------
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
   
  I hope this willl help you for sharing yoru files !
  
Good courage !
 
Pat'

---

### Post by unixfudotnet on 2005-11-22
[QUOTE=pompeyjohn]hi there,

thanks for the response.

Knoppmyth is a debian based distro - you can check it out here 

[it rocks]("http://www.mysettopbox.tv/knoppmyth.html")

I am running Ubuntu, so nautilus it is...

I can ssh to it through the location bar, but I just tried to create a connection to it and add it as a 'place.' Something went wrong though and it doesnt connect. I guessed that the port would be 25, but not sure about that. Now I cant delete this incorrect place from the place list. How can I do that?

The reason I asked about all this is because I was wondering if there was a fstab type file for network shared folders.

cheers[/QUOTE]


ssh runs on port 22. You can add a location from the gnome ubuntu menu at the top.

---

### Post by chaumurky on 2005-12-01
[quote=unixfudotnet]I am not sure what knoppmyth is, yet if it is a linux/unix, you may use nautilus or konq to browse the other machine via http, ftp, or ssh.

konq -> fish://username@server.name.net/
  * this will start an interactive ssh session
        
nautilus -> ssh://username@server.name.net/
  * this will start an interactive ssh session

You may use this method to drag and drop files around over secure channels.

If you wish to do this without both sides being linux/unix, you may setup Samba and mark directories/files as shared. There are several Samba howtos out there, and Ubuntu provides a Samba gui tool by default (I think). Then in linux you can smbmount (provided smbfs support is in the kernel) the share to your local filesystem and browse (nautilus and konq support this, as does firefox if you compile it in) or browse regularly in Windows as you would another Windows machine with shared folders.[/quote]

If the server I'm connecting to requires a key (passwordless), how do I do that with nautilus?

---

