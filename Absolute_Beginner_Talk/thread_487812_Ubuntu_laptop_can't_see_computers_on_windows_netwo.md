---
title: "Ubuntu laptop can't see computers on windows network in house"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by beginner3228 on 2007-06-29
I have Windows XP on my home computer and I just began using Ubuntu on my laptop.  I tried to set my laptop to be able to print from the printer connected to my home computer, but the Ubuntu partition on my laptop cannot "see" any computers on the Windows network.  I can share files and printers when I try from the Windows partition on my laptop.  Any ideas on how to fix this and be able to print from the home computer's printer when on Ubuntu on my laptop?

---

### Post by overdrank on 2007-06-29
> **beginner3228 said:**
> I have Windows XP on my home computer and I just began using Ubuntu on my laptop.  I tried to set my laptop to be able to print from the printer connected to my home computer, but the Ubuntu partition on my laptop cannot "see" any computers on the Windows network.  I can share files and printers when I try from the Windows partition on my laptop.  Any ideas on how to fix this and be able to print from the home computer's printer when on Ubuntu on my laptop?

HI I hope this will help, If you go to system,administration, shared folder there it should prompt you to install the software to share then you can choose the folders to share. You may need have your windows system with the printer on at that time and then do a restart and that should get you where you can print and share. Good luck! :D

---

### Post by lawr_rawr on 2007-06-29
How are you trying to find the windows PCs? By name or IP? I was able to connect to shares by IP, but not name, until I did the following to enable NETBIOS name resolution:
```
sudo apt-get install winbind
```
Then edit /etc/nsswitch.conf and modify the hosts line by adding wins to the end:
```
hosts: files dns mdns wins
```
From there, you should be able to ping the windows machines by name.

---

### Post by lintoon on 2007-06-29
Is samba installed and running
Is your Ubuntu in the same workgroup as the windows box.

---

### Post by martinw89 on 2007-07-06
Hi,
I've been helping with this problem in person.  It's a really really weird issue.  Samba is installed and running fine.  Ubuntu is set to use the same workgroup as the other (windows) computer.  The Windows computer with the printer is of course on.  If the Ubuntu box is restarted into Windows the two computers can share files and printers normally.  However, Places -> Network in Ubuntu does not show the Windows computer.  We tried both suggestions with no luck.  Installing the Samba service seemed like it would be the problem but unfortunately it did not fix anything, and on a side note I can access shared printers on my computer without going through the process to install the Samba service.  lawr_rawr your help is appreciated as well but that also did not work.  Any other ideas would be really appreciated.

---

### Post by Linux Daddy on 2007-11-21
I had the same problem and I solved it by adding my windows username and password as a SMB user on the UBUNTU computer that could not see the other computers on the windows network.

```

sudo smbpasswd -L -a USERNAME	(set a password)
sudo smbpasswd -L -e USERNAME	(enable user)

```

After I did that, I could see all the computers in my windows network. 

I followed the instructions here:

[http://ubuntuforums.org/showthread.php?p=3800899]("http://ubuntuforums.org/showthread.php?p=3800899")

P.S. This is my first post so I hope this helps

---

### Post by jonandrews on 2007-11-22
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

I realise this may not help if you have a wireless issue, but otherwise it could be helpful.

Good Luck

---

