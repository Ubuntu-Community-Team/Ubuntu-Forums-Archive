---
title: "File server set up"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by zino1 on 2006-03-15
I am very new to Ubuntu just crossing over from Windows.

I want to set up a file server for my network.

I know in windows it was all GUI driven.

How do I set this up in this OS?
Do I need Samba?

How will I be able to get to it from the internet using WSFTP Pro(or one of the others)?
Do I need to open ports for use as in Windows?

Sorry, I am sure this is a much more involved process, but I see to be lost.

---

### Post by beercz on 2006-03-15
[QUOTE=zino1]I am very new to Ubuntu just crossing over from Windows.

I want to set up a file server for my network.

I know in windows it was all GUI driven.

How do I set this up in this OS?
Do I need Samba?

How will I be able to get to it from the internet using WSFTP Pro(or one of the others)?
Do I need to open ports for use as in Windows?

Sorry, I am sure this is a much more involved process, but I see to be lost.[/QUOTE]
Hi zino1

Welcome

You can indeed set up ubuntu as a file server for windows client machines

You need to install samba - have a look at [https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29")
This may also help: [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

It really isn't that difficult.

When you have set it up, to remotely access your samba machine from windows you can use winSCP, get it here: [http://winscp.net/eng/download.php]("http://winscp.net/eng/download.php")

No need to open ports in windows and don't apologise :-) (no need)

Good luck!  Post back if you have further questions - we all had to start somewhere and always glad to to help if we can.

---

### Post by zino1 on 2006-03-16
beercz,

Thank you for your response. I have been able to make some changes from the links you provided.


I can not see this machine and the windows machines from this box when I go to <places>, <Network Servers>. before I could only see the windows boxes.

I cannot however see this box yet from the windows machines in my network. I have 4 windows machines networked and they can all see and talk to each other, yet no go witht he Ubuntu box. I am behind a router and I can ping this box from windows but cannot see it in my network places

Also, I did not see how to set this up so that I could use an FTP program (ie FlashFXP, WS_FTP Pro).

I downloaded winscp376setup.exe to my desktop and when I doubleclick it to run I get "can't display location" "Couldn't display "/home/zino1/desktop/winscp376setup.exe"

---

### Post by zino1 on 2006-03-16
[QUOTE=zino1]beercz,

I can not see this machine and the windows machines from this box when I go to <places>, <Network Servers>. before I could only see the windows boxes.

I meant to type I CAN see this achine and the windows machines from this box when I go to <places>, <Network Servers>. before I could only see the windows boxes.

---

### Post by zino1 on 2006-03-16
[QUOTE=zino1][QUOTE=zino1]beercz,

I can not see this machine and the windows machines from this box when I go to <places>, <Network Servers>. before I could only see the windows boxes.
[/QUOTE]

I meant to type I CAN now see this machine and the windows machines from this box when I go to <places>, <Network Servers>. before I could only see the windows boxes.

Also, I see a utility called swat that will cnfigure Samba, yet it does not seem to be installed on this machine. Is it supposed to be?

---

### Post by beercz on 2006-03-17
You need to look at /etc/samba/smb.conf - this is the samba configuration file.  I tend you use an editor like vim to edit this file, but I guess you can use swat - I have never used it.

In a terminal window I guess you could do:

sudo gedit /etc/samba/smb.conf

This will open the text editor and allow you to configure your samba server.

Restart the samba server with smbd;nmbd (I think) after configuration

You add samba users with smbpasswd -a <<username>>

See: [http://ubuntuforums.org/showthread.php?t=2389]("http://ubuntuforums.org/showthread.php?t=2389")

Good luck and feedback.

---

