---
title: "networking issues"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-02-02
i am on a LAN in my house.  my housemate and i sometimes need to share files.  he has XPpro and i have ubuntu.  our computers don't see eachother.  what do i do?

---

### Post by galgoz on 2006-02-02
I hope someone gives an amazingly simple answer to this, I worked on this for days and is a large part of why I dual boot again instead of just having ubuntu installed.  Boy do I want to leave windows for good.

---

### Post by steve.horsley on 2006-02-02
In Nautilus, right-click on a folder and choose Share Folder. I have never used this, but the questions the wizard asks look easy and comprehensive to me.

To connect to your firend's computer, use nautilus and the menu option File->Connect to Server. Select a service type of Windows Share, and enter her IP address as the server name. This works for me.

---

### Post by insub2 on 2006-02-02
thank you sooo much steve.horsley

---

### Post by MartinG on 2006-02-02
Can you ping each other?  If not, sort out the firewalls first. Then to get networking, check out the Unofficial Guide:
[http://makuchaku.info/amnesty/#networking](http://makuchaku.info/amnesty/#networking)

Some of what's in the guide is more than you need; in brief, you need to install samba and smbfs and configure the system (workgroup name, sharing rules etc.), and you need to designate shared folders on both machines.  KDE has a useful GUI for samba configuration (in kcontrol), I don't know about Gnome.

If there are problems it helps to disable all firewalls etc. to set up the basics (isolate the LAN from the Internet if possible), and once the network itself is working properly get the firewalls configured; a lot of my apparent network problems have been firewall-related.

---

### Post by TechSonic on 2006-02-02
Just trash Windows on that other computer and put Ubuntu on it, there problem fixed :D

---

### Post by insub2 on 2006-02-02
[QUOTE=TechSonic]Just trash Windows on that other computer and put Ubuntu on it, there problem fixed :D[/QUOTE]

hahahahhahahahahahahahaha  niiice.

---

