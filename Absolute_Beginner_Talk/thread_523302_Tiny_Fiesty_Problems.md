---
title: "Tiny Fiesty Problems"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by adewale on 2007-08-11
My friend just installed kde from synaptic and i noticed that the kdenetwork systray was missing all attempts get it was missing. Is there a way to get this systray as its very useful. 
Also i made my /home  shared using system->Administration ->Shared Folders. I choose Nfs since my friend was also running ubuntu and yet his laptop couldn't see mine. I also tried using vnc but it complianed that host (me) wasn't found.
Also i went to network:/// yet his pc didn't show there and likewise mine didn't show up in his too.
Please is there an effective way of doing this ?
Please note that we used an ethernet cable. Also we both use dialup so our ip's change regularly 
Thanks am off to bed now

---

### Post by halitech on 2007-08-11
do you have the network names the same? are you using a router or a hub to connect or a cross over cable? have you checked the IP addresses on the network cards (eth0 normally) can you ping each other (if you know the IP addresses)?

---

### Post by adewale on 2007-08-12
i just came back thanks. we don't have a router. its the normal lan cable we tried using. and we both use dialup to connect to the internet so that changes my ip. Constantly when i dial out. thanks

---

### Post by zeifertstc on 2007-08-12
I would recommend the purchase of a broadband router for local communication with systems even though you have dial-up internet. 

The hub would allow you both to connect to each other. You'll probably want to make sure that you set each computer on the same network (ie., WORKGROUP, MSHOME etc) when setting up the network portion of the OS. Also, I've never been too successful in getting nfs to work with linux but Samba will allow you to connect to linux boxes as well as windows boxes for file sharing across a local area network (LAN).

Otherwise, I do not know if linux can handle connecting directly to another computer with patch cables as neither computer can assign the other with an IP address. It may require additional packages to be installed if that is the method you need to connect. But you can acquire a router from NETGEAR for about $55 from Radio Shack or a Belkin from Wal-Mart. Radio Shack usually will have special deals going on. I was able to get a router from Radio Shack for around $55 with instant rebate and a wireless PCI card for my desktop computer to go along with it and spent a little over $100 that day. If you want a quality router, though, spend a little more and get yourself a wireless g router from Linksys and you'll be able to connect to computers in your house (wired and unwired) as long as they're on the same network. 

You'll need Samba and smbclient and make sure that your file manager (gnome's file manager works by default but konqueror works best in my opinion) can handle samba after it is installed.

---

