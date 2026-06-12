---
title: "Total Beginner at Networking. FF/XP"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-05-27
I have Feisty on my desktop, which is wired to my router. My fiancée has a Win XP laptop, which accesses Internet wirelessly, via the same router. Our printer is wired to my computer. I'd like to share the printer, and hopefully files with the laptop. I don't mind doing some reading, but I'm having a hard time figuring out where to start, because everything I've found here related to connecting to a windows server.  I want Ubuntu to be the server, and while I've heard of Samba, I don't have the slightest idea how to use it or what I need to do in the Win laptop to make this work. The printer is more important than the files, but if it is just a step or five more, then I'd like that too. Can someone send me in the right direction for my particular situation? Reading all of these instructions for different setups seems to be leading me in the wrong direction.
Thanks

---

### Post by seshomaru samma on 2007-05-27
perhaps[ this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_home_folders_with_read_only_permission_.28Authentication.3DYes.29") is what you need

---

### Post by dave-5B on 2007-05-27
Just about everything you need can be done through the System menu

This website is by Ubuntu bible:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

To install samba
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)
(samba is how you share ffolders & printers so they are visible to windows systems, you dont need top do anyting to the WinXP laptop samba will appear just like another windows system)

printers can be added: System > Admin > Printing

if you dont like typing at the command line: 
when it says "sudo apt-get" or anything about repositories you can do the same thing through System > Admin > Synaptic Package Manager (this is just a GUI for apitude / apt-get)

you can also go System > Admin > Shared Folders instead of manually editing the samba config file (i think)

hope that helps

---

### Post by coldstatue on 2007-05-27
Thank you. I will be trying this out today.

---

