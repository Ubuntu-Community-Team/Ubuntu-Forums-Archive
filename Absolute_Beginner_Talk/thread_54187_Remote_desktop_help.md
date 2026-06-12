---
title: "Remote desktop help"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by gtstdiy on 2005-08-03
Hi there, I've been setting up my grandad with a computer - using kubuntu at the moment (mainly because kmail can be made to be very simple)... 

Anyway, I'd like to get him out of a mess with out having to go over to his house. 
Is there a way that I can have a Remote Desktop setup so that he can simply click one button on the taskbar or something, and his computer will automaticly accecpt a dial up connection from my computer to his, granting me whatever privledges (maybe root). I could then fix it up and log off, and he could just click another button to disable his computer answering the phone.

I am good with comuputers but know rather little with linux - but im sure with help I could write a script or something.

Any help or thoughts anybody?

Lincoln

---

### Post by megaultraninja on 2005-08-03
ssh username@ip

---

### Post by gtstdiy on 2005-08-03
Sorry, can you explain that a little more? will that make the modem answer an incomming phone call?
cheers.

---

### Post by cwaldbieser on 2005-08-03
If your grandfather has broadband, the above command will let you connect to his computer via secure shell.  That was my first thought as well, but then I considered that maybe you want to dial in because he doesn't have a broadband connection.

It has been a while, but does kppp have some sort of configuration option where it can be set to simply put the phone in auto-answer mode?  Since this is just a front-end for pppd, I am pretty sure there is some way to script this to happen, but the answer eludes me at the moment.

Once you establish the PPP connection, you can use ssh, VNC, X-forwarding, etc. to access and maintain the remote PC.

---

### Post by megaultraninja on 2005-08-03
ssh (secure shell) will enable you to remotely log on your fathers computer though an encrypted channel (assuming he is online).

so jump into the terminal type 'ssh' and then your fathers username, and then '@' and then your fathers ip address or host name.

so if your father's user name is 'ubuntu_user' and his ip address is '242.1.2.3' then the command would be:
'ssh ubuntu_user@242.1.2.4'

you will then be connected to your fathers computer in the shell. you can connect to X this way too. but im a little rusty at this, so you should probably double check this (sorry)

'ssh -X ubuntu_user@242.1.2.4'
'nautilus ~ &'

that should open a file manager at his home directory.

[QUOTE=gtstdiy]will that make the modem answer an incomming phone call?
cheers.[/QUOTE]
I'm not sure i understand this question



NOTE: you may have to install 'sshd' ('apt-get install sshd')

---

