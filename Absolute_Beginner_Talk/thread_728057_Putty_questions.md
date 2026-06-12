---
title: "Putty questions"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-18
Checking to see if I'm understanding what Putty is... or at least what Putty is or could be used in my situation.

I have Ubuntu server up and running, with Samba working as well.

When I get the server into the proper location, I do not want a monitor, mouse and keyboard attached.

The server is connected to my home network, of which I have a Win XP also hooked into.  Would enable me to administer Ubuntu from my win XP desktop?

It sounds like I can run a Win XP Putty app on my XP computer to be able to access/remote into the Ubuntu server... correct?

If so, are there one or many Win XP Putty apps out there?  If many, what some of the better apps?

Thanks!

---

### Post by Oldsoldier2003 on 2008-03-18
> **BlizzofOZ said:**
> Checking to see if I'm understanding what Putty is... or at least what Putty is or could be used in my situation.

I have Ubuntu server up and running, with Samba working as well.

When I get the server into the proper location, I do not want a monitor, mouse and keyboard attached.

The server is connected to my home network, of which I have a Win XP also hooked into.  Would enable me to administer Ubuntu from my win XP desktop?

It sounds like I can run a Win XP Putty app on my XP computer to be able to access/remote into the Ubuntu server... correct?

If so, are there one or many Win XP Putty apps out there?  If many, what some of the better apps?

Thanks!
in a nutshell yes.[ PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") is the "accepted standard" for most windows users and it will do pretty much everything you need to do . you can just google for PUTTY and if you prefer a different terminal emulator there are other programs out there that will work as well.

Try to stay away from telnet though- use ssh to connect to your server instead of telnet because telnet sends passwords in clear text.

---

### Post by BlizzofOZ on 2008-03-18
Thanks... that is what I thought.

Went to that page and viewed the FAQs...  I see that Open-SSH is not quite supported as SSH-2.

I believe I had to install Open-SSH for Samba file serving... does that also install SSH-2 or do I have to install that.

If so, how?

---

### Post by BlizzofOZ on 2008-03-18
What is better SSH-2 or VNC?

Does Putty VNC or is that a sperate app.

Does VNC really fit what I need it for?  Both computers will be behind a router and firewall.

---

### Post by Xiong Chiamiov on 2008-03-18
As I understand it, VNC is for remote desktops, meaning that you see the screen of the other computer, and control is with a mouse and gui.  When you SSH into another machine, you're limited to simply a terminal window.  Which one you choose depends on your needs; remote desktops have more flexibility, but are considerably slower.

---

### Post by The Cog on 2008-03-18
> **BlizzofOZ said:**
> Thanks... that is what I thought.

Went to that page and viewed the FAQs...  I see that Open-SSH is not quite supported as SSH-2.
I don't know what you mean here. I'm not aware of any support problems with openssh.> 
I believe I had to install Open-SSH for Samba file serving... does that also install SSH-2 or do I have to install that.

If so, how?
No. SSH and samba are entirely different things. Samba serves shares using MS's proprietary protocols. OpenSSH uses the SSH protocol.


Also be aware that SSH doesn't directly offer a GUI - just command-line and file transfer like telnet and FTP. For a GUI, either use VNC (which can be tunneled through SSH) or find an X server for your desktop and let SSH tunnel X.

---

