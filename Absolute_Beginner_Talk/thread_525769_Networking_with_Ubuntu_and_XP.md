---
title: "Networking with Ubuntu and XP"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by ripple01 on 2007-08-14
Hi,

I currently have Feisty installed on my desktop and everything is working great. I have a Linksys wireless router attached to my desktop which my Laptop uses for the Internet. I am running XP on my laptop and I can use my laptop to connect to the internet just fine. I am running into problems on sharing files between the two computers. I have two 160GB HD's installed in my desktop, one with Ubuntu and the other is formatted in NTFS and has all my movies, music, etc. I have set the NTFS drive as a shared drive and installed Samba. 

On my laptop, I can see my desktop listed in My Network Places. However, when I double-click on my dekstop, it brings up a username and password prompt. I tried my Ubuntu login and it doesn't work. 

Can anyone point me to a way forward?

Thanks,
ripple01

---

### Post by st33med on 2007-08-14
It possibly wants your XP password for your network. I'm not entirely sure, but check your Windows Network on Windows XP to check a password. I think investigating through the propeties of the network (Right-click -> Properties) will reveal something.

---

### Post by Blutack on 2007-08-14
The evil samba bug strikes again!  Its the gnome habit of simplifying stuff - great, but occasionally they take out the functional equivalent of the "ok" button.
do
gksudo /etc/samba/smb.conf
find the line
;   security = user
and replace user with share.
Then restart samba
sudo /etc/init.d/samba restart

---

### Post by p_quarles on 2007-08-14
No, it wants the Samba username, which probably hasn't been enabled yet. 
```
smbpasswd -a *username*
```
Setting up Samba is actually kinda complicated. Try following the tutorial linked below, and ask here if you have questions about it:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by ripple01 on 2007-08-14
Thanks, p_quarles, that is exactly what I needed to do. It seems to be working fine. 

However, Windows is not seeing my printer attached to my desktop. Anyone point me to a guide to using an Ubuntu printer on a XP system?

Thanks,
ripple01

---

### Post by p_quarles on 2007-08-14
Did you setup print sharing in smb.conf?  Make sure that's working, first, and then you can configure the printer using CUPS. On the Ubuntu box, open a browser and go to localhost:631.

That will take you to a pretty great graphical interface for configuring your printer(s).

---

