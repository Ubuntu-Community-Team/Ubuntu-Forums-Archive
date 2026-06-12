---
title: "Connect to Shared Mac DVDROM"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by raq1025 on 2008-12-16
Hello all,

I am a relative newbie to Linux & Ubuntu. I have installed 8.10 on a Dell D420 that does not have a CDROM or DVDROM drive. I have an Intel iMac that I'd like to share the DVDROM from. I have enabled Sharing for "DVD or CD Sharing" in the iMac's preferences. I have also turned on "File Sharing" which should turn on SMB sharing. 
When I double click on Network, then Windows Network I see nothing. When I try to connect directly to the IP (SMB://192.168.1.100) I get "Cannot display location."
Anyone know what I need to do to accomplish what I want?

Rich Q.

---

### Post by tiresia on 2008-12-16
If you want to use a GUI, you can try with Places > Connect to server 
There you must choose Windows Share (= Samba) > and give the ip address of the imac and the user name. Most probably you need to give also the 'share'. Aftewards you will be asked for the password.

---

### Post by raq1025 on 2008-12-16
Yes, I've tried that and its when I get the "Cannot display location" error. Is there something else I'm missing?

---

### Post by cyberdork33 on 2008-12-17
> **raq1025 said:**
> Yes, I've tried that and its when I get the "Cannot display location" error. Is there something else I'm missing?
Did you add anything to the list of shared items when you turned File Sharing on?

Also, I am not sure of the format that "DVD or CD Sharing" uses. It may not be possible to use that in combination with Linux.

---

### Post by Heinzelotto on 2008-12-17
try this:
[http://www.macosxhints.com/article.php?story=20060420105632844](http://www.macosxhints.com/article.php?story=20060420105632844)
then you should be able to access the dvd drive from Linux by going to the "Public"-directory of the mac

---

### Post by Return Privacy on 2012-08-14
Bump!
This was never solved. I am having the same problem.
I did post a new question in Server Platforms.:confused:

---

