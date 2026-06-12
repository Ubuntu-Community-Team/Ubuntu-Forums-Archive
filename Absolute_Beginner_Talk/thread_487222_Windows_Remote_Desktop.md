---
title: "Windows Remote Desktop"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-06-28
I'm having a problem. I can't tell if this is on the Windows side or the Ubuntu side. Here is my situation. I have a laptop running Ubuntu Gutsy. I also have multiple desktops running Windows XP Home Edition. I know I can use VNC to connect remotely to the desktops, but that involves installing a server on them, which is not possible in my situation. So instead, I wanted to look into connecting through the windows remote desktop protocol (RDP). It looks like I can use rdesktop or Terminal Server Client to connect through this. However, when I enter in the IP address in Terminal Server Client, I get "ERROR: connect: Connection refused". Based on prior knowledge, I assumed this meant that I either hadn't enabled a certain settings in Windows, or the firewall is blocking it. I am not sure though. If someone knows what might be preventing me from connecting, could you please let me know? If it is the firewall, what port should I unblock? If it is a settings, where is it and what should it be set to?

---

### Post by ellisdee on 2007-06-28
Are your other machines able to RDP to this particular server?

You may not have enabled RDP on the server. To do so you will need to go into Control Panel-System-Remote and enable remote desktop.

Once you have done this you will need to setup a User account with a password so that it will prompt when you RDP to this machine.

These are just the initial steps in setting up RDP if you have already done this I would then look at firewall settings.

---

### Post by bruce50 on 2007-06-28
I do not believe that XP home Edition can act as an RDP Server.  You can use RDP Client from XP Home to connect to a XP Pro or Server machine but not the other way around.  Right click on My Computer, click the Properties selection and look on the Remote tab.  On XP Pro there is an entire section on enabling remote access to the computer.  The only thing you can enable on XP Home is the completely useless Remote Assistance.

---

