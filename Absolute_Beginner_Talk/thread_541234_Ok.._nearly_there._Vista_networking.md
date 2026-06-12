---
title: "Ok.. nearly there. Vista networking"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2007-09-02
Right I've followed these steps, and the last step I am a little unclear on..
(\\<ubuntu_host>\<share_name>) what do I out in here? Sorry if it's a stupid question but I'm stumped.
Thanks
(I used the following post for help [http://ubuntuforums.org/showthread.php?t=506725](http://ubuntuforums.org/showthread.php?t=506725) 


1. this will install samba, a protocol which allows windows and ubuntu to easily share files ("samba - A Windows SMB/CIFS fileserver for UNIX") ... the command i gave should be run in a terminal window, it will allow you to easily install samba ... you can fire up synaptic and install it that way too ...
2. you need to (possibly) make a few configuration changes to samba, since everyone's network is different ... the WORKGROUP defaults to either MSHOME or WORKGROUP and not everyone uses either one ... it's one of the 1st entries, so you should see it straight away ... there might also be some ubuntu GUI for configuring samba, not sure ... you can use any editor of your choice, command line (nano, vi) or GUI (gedit, kate, etc.) - just make sure you have root access (i.e. use sudo) ...
3. this is a big step a lot of people miss, and it's understandable - not something you'd generally think about ... samba (on unix) doesn't just let anyone connect - so the command i gave will add a new user account to use samba ... i generally have my ubuntu/windows password on my local network be the same, so it's easy ... if you don't do that, you just have to add another step when using "map network drive" ...
4. this is done in vista, and allows you to use the share you created in ubuntu as a disk drive in vista ... you just navigate to "map network drive" and enter the path to the share (\\<ubuntu_host>\<share_name>) and the drive letter you want to use ... if you use the same U/P combo between the two it should connect straight away ...

---

### Post by dasunst3r on 2007-09-02
With your Samba server nearly working, you might want to consider installing SWAT also.  It is a web administration tool.  After installation, you can access it via http://{address}:901

---

