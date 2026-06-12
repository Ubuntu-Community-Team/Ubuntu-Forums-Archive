---
title: "Accessing Samba Server from my W2k Network"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by StevenF on 2005-11-18
Hi, I hope someone can help me out with this. I have a samba server connected to my W2K network. I can see the server in the MShome directory of my Network Places. I try to open to explore and it asks for a network password. 

It shows a Windows Dialog: **Enter Network Password** 
underneath it shows \\Ubuntu
Then it has a Connect As: input area and Password: input area

I've tried my windows network login, the ubuntu machine login but nothing works. 
I want to use this box as a file server on the network for five or six users to access. I'd prefer that the users not have to enter a password at all since it is a local server. Samba wasn't originally installed and I couldn't see it from my windows server prior to installing. Now I can see it but can't access it.
I'm getting very frustrated at this point.
Any help will be greatly appriciated!

---

### Post by herrpoon on 2005-11-18
Hi there, I'm not sure what version of Ubuntu you're using although I imagine the setup for samba would be the same for both 5.04 and 5.10, ubuntu guide has an excellent guide for setting up exactly what you want:[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

I am in a similar situation to you whereby there are 4 or 5 win machines which need to be able to access my ubuntu box, so I have set up samba like this:

How to share public folders with read only permission (Authentication=No)

Then I'll create a link to say /share/music or whatever and put it in the public folder.

---

### Post by StevenF on 2005-11-18
Thanks for the quick reply. I'm using 5.10, Is there a way to do this from the networking console? Do I have to create a Group on the Samba Server
and then add users to the Group? As you can probably tell this is all very new to me.

---

### Post by ed_d on 2005-11-18
Go here:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)
Scroll down to the samb portion.

If you just want to share certian folders, then click System>Administration>Shared Folders
Add a new share and then tab "allow browsing folder"

Should be all good then

---

