---
title: "Sharing folders and printers"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by fhqwhgad on 2007-05-09
Hi,
I've just spent ~1 hour trying to install my crappy Brother printer, and now it finally works.
There's just one problem though, none of the computers on the network can see it.
so how do i actually make it visible on the network?
I've set the cups web-interface to share published printers and in my gnome-printer window, i've enabled shared printers aswell.

Also, i've shared a folder with my windows network. Only problem is, when i try to enter the folder from a network computer, it asks for username/password. I'd like anonymous access to the folder and the printer, from my local network.

Also, i can't even use my userlogin to access the network share, so i have no idea what user/password it wants.

Thank you.

---

### Post by Scunizi on 2007-05-09
Although I can't answer your question specifically, you need to look into Samba.  Samba is what will allow others (win machines) to see your printer and folder shares and access them.  Check out [https://wiki.ubuntu.com/ComprehensiveSambaGuide?highlight=%28samba%29](https://wiki.ubuntu.com/ComprehensiveSambaGuide?highlight=%28samba%29) and see if that doesn't point you in the right direction.

---

### Post by fhqwhgad on 2007-05-10
Yea i got samba installed and sharing the folder through the GUI was really easy. For some reason it just needs a password i don't know.

I will check out the guide later and report back. Thank you.

---

### Post by mbradlcu on 2007-05-10
I set mine up using this site:
[http://www.ubuntuforums.org/showthread.php?p=2240806](http://www.ubuntuforums.org/showthread.php?p=2240806)

If you're trying to connect via other *nix machines this should work:

On the client machines:
Allow network printing
Goto: System > Administration > Printing
then goto: Global Settings > Detect LAN Printers, and make sure it is ticked.
Browsing On
Specify the CUPS server
vi /etc/cups/client.conf
and add the line:
ServerName 192.168.0.150
substituting your printserver's IP address or name.

---

### Post by fhqwhgad on 2007-05-10
I'm using windows clients.

I got the shares working fine now, and the printer is shared aswell. I can see it, and connect to it (sort of) from the windows clients, but i can't print. It just says "Access denied, unable to connect" when i open the printer queue.

I don't get it at all. I've got anonymous shares in samba that works fine.

---

### Post by fhqwhgad on 2007-05-11
Noone knows how to make the printer work?

---

### Post by tagra123 on 2007-05-13
> **fhqwhgad said:**
> Noone knows how to make the printer work?


Good luck getting the printer sharing  to work using the documented methods. I'm taking a few minutes trying to route some of the unsolved printing posts to my workaround until something gets fixed by cups or ubuntu.  None of the programmers want to admit there's a problem. Go figure. 


[http://ubuntuforums.org/showpost.php?p=2591426&postcount=8](http://ubuntuforums.org/showpost.php?p=2591426&postcount=8)

---

### Post by fhqwhgad on 2007-05-14
Thank you, but how do i connect to the pritner from a windows client? It doesn't seem to appear on the server shares.

---

