---
title: "Connect from Windows XP to Ubuntu dual boot PC NTFS shares"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by omega13lives on 2007-04-07
I'm sure this is possible, but I have no idea where to start.  As the Title suggests, I want to connect from my second Windows XP machine to shares on my primary computer, using a dual boot to Ubuntu with several NTFS Windows shares (where the movies are).  I will try this, this weekend, and would accept any useful suggestions.  tx

---

### Post by Austin_KW on 2007-04-07
You want to install the samba server, then you can create windows shares for files and printers
see installing samba and configuring your pc as a server in

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by omega13lives on 2007-04-07
I'm still confused.  Ubuntu already has the Samba installed (but not the server) yet I don't know how to "see" my Linux computer from my Windows one.  Then I'll see if my shares are visible.

---

### Post by Austin_KW on 2007-04-08
Samba will let you see and browse your windows shares that are shared from your windows PCs. 

If you want to see files on your linux computer then you will need to install samba server and configure the shares (whatever files/directories/disks and printers) you want to share. XP runs a similar smb server when you boot XP, but its shares are only visible when XP is booted. 
You can create the same shares or different ones under samba server when you boot linux. This is done either by editing /etc/samba/smb.conf or using a GUI such as kcontrol, or I think in gnome system->administration->shared folders. I found it easiest when I started to first use the GUI and see what it had done to /etc/samba/smb.conf. Now I just edit the file /etc/samba/smb.conf and restart samba server with "sudo /etc/init.d/samba restart" or "sudo /etc/init.d/samba reload"

---

