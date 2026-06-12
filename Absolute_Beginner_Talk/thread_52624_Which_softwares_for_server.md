---
title: "Which softwares for server?"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by sooqing on 2005-07-28
Hi!

I will be setting up an ethernet network for my class of 50 desktops.. all, including the server, will be using linux (may be Fedora, Ubuntu, etc..) and I would like to configure the network such that all users have their own account, ie. they can login using any of the 50 PCs to their individual account and no one else can access any PC without an account.. the PC are sort of a dumb terminal as I don't files created by them to be on the PC but on the server.. so if they go to terminal A to download a mp3, they can logoff and go login to terminal B and find the same mp3 in their home directory.. 


So what are the softwares I will need to install?

---

### Post by sunwave on 2005-07-28
[QUOTE=sooqing]Hi!

I will be setting up an ethernet network for my class of 50 desktops.. all, including the server, will be using linux (may be Fedora, Ubuntu, etc..) and I would like to configure the network such that all users have their own account, ie. they can login using any of the 50 PCs to their individual account and no one else can access any PC without an account.. the PC are sort of a dumb terminal as I don't files created by them to be on the PC but on the server.. so if they go to terminal A to download a mp3, they can logoff and go login to terminal B and find the same mp3 in their home directory.. 


So what are the softwares I will need to install?[/QUOTE]

 It depends on how your Infrastrukture will be. If you like Severbased Computing (TerminalServer) you should take a look at NXServer:
[http://freenx.berlios.de/](http://http://freenx.berlios.de/) 

If you intend to Develop a Client/Server Infrastrukture what are your needs?
How do you plan to Setup and configure the Clients. Do you have planned to have a standard Client or hybrid linux Clients? Or do you eventually wanna allow Windows-Clients to connect to the network ? What about IP-Adress ? Static or is DHCP planned.

You should design your Concept on paper first and list all your needs and requirements down. 

After that post it, so we can help with ideas and Infrastrukture designs.

I think we should then splitt in two different groups. Server and Client.

Then we have to define the required Server-Software and Configuration for Server and the same procedure for Client.

Do you have experience in planning and designing Infrastruktures ? If not you should contact any System-Administrator to help Building this from Scratch or you end up in a mess.

---

### Post by sooqing on 2005-07-28
oh.. i just found out.. use NIS.. tks anyway!

---

