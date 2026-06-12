---
title: "accessing WinXP (vmware) from Ubuntu"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by n1tro on 2006-03-08
Ok, this forum is awesome and in a short period of time, I have the perfect setup. I got Ubuntu running in all it's glory with eye candy such as 3Ddesktop, gdesklets, etc... Even got Windows XP running through VMware with webcam support so I can do videochats. Now the last thing I need to be able to do is be able to access the files in the VMware space of XP through Ubuntu.  Any help is appreciated! Thanks.

---

### Post by andrewsawyer on 2006-03-08
The easiest way would be to set up your Windows Desktop (or even entire My Documents directory) as shared, and then access it through Ubuntu as a Windows networked computer.

Note: I'm not sure if you can do this if you have confirgured the VMWare networking as NAT - I think Windows has to be allocated it's own IP address from the DHCP server/router.

---

### Post by n1tro on 2006-03-08
I've already made the documents directory and another directory shared but it still doesn't see it on the network. I do have the NAT setting in VMware because from another user, you have to have that in or the VWware XP won't have access to the Internet. Anyone else have insights on this matter? All I need is to get this done and fix Ubuntu not connecting to my wireless router with WEP enabled. :(

---

### Post by n1tro on 2006-03-08
I got it going! Double clicking on the network icon under Places brings up a login screen. Just blank out the name and password and leave MSHOME as the domain and it will see the shared drives in the virtual XP setup under VMware. Almost in bliss mode now!!! Just the wifi issue...

---

