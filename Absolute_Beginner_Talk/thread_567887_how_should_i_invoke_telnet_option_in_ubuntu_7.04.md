---
title: "how should i invoke telnet option in ubuntu 7.04"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Aamir Aziz on 2007-10-05
i' m using ubuntu 7.04 and my pc is connected with LAN.  i'm interested to access my pc  through telnet from anywhere in LAN. how should i turn on the access of telnet in my OS. 
          or
       is there another way to access my pc from windows XP. because everyone is using windows XP and i can not access my PC.  

       can ubuntu 7.04 be accessed remotely by windows XP. if possible how should i turn on this feature??

---

### Post by cmnorton on 2007-10-05
Whether you use telnet or not depends on what's in front of your LAN, like a good firewall. Ubuntu comes with sshd running by default, at least it did for me in 6.06, and I'm on Fesity now.  

If you need terminal emulation, there is at least one good product for Linux, Ericom's PowerTerm Interconnect (for Linux); that has telnet and ssh protocols built in. If you're accessing this system from Windows, Van Dyke's SecureCrt provides telnet and ssh emulation.

If you want telnetd, you've got to download it, and make sure it is enabled in /etc/inetd.conf. I've forgotten if I had to do anything else to get it working. Certainly you would not want to access via telent from outside your firewall.

---

### Post by Matakoo on 2007-10-05
> **Aamir Aziz said:**
> i' m using ubuntu 7.04 and my pc is connected with LAN.  i'm interested to access my pc  through telnet from anywhere in LAN. how should i turn on the access of telnet in my OS. 

If the LAN is exposed to the Internet, you don't want to enable telnet access unless you have a good firewall in place. You want ssh, and properly configured.

To begin with, sudo apt-get install ssh

After that, there are plenty of good how-to's on how to properly secure it. For windows, putty is a decent (not to mention free) ssh-client.

> **Aamir Aziz said:**
> can ubuntu 7.04 be accessed remotely by windows XP. if possible how should i turn on this feature??

Sure it can, but it depends on exactly what you want to accomplish. Control your Linux desktop? Take a look at VNC. There are Linux tools to view Windows desktops using the built-in remote desktop of Windows, but I'm not sure if there is a remote desktop server for Linux (one that the Windows client knows how to speak to that is).

If you just need to access your files, take a look at Samba. It can be a nightmare to configure if you're not used to Samba and/or Windows networking terminology though, but it does work once setup (better than Microsoft's own offering IMO). Oh, and the firewall is a must here too.

---

### Post by hyper_ch on 2007-10-05
if it's just file sharing then I'd go for SSH/SCP/SFPT instead of samba...

---

### Post by Matakoo on 2007-10-05
> **hyper_ch said:**
> if it's just file sharing then I'd go for SSH/SCP/SFPT instead of samba...

Well, I would say that depends. If you want the most secure solution, sure. Then that is the way to go. If you want a solution that is more integrated in a windows-environment, maybe not. Or just wants a more convenient solution for that matter.

For example, if you want to have access to music-files stored on a Linux-box, can you access them straight from the file-selector in say WinAMP? Last time I checked, it wasn't possible unless you had "mapped" either a smb-share or ftp-share that the Linux-box provides. 

Then again, it may be possible using some third-party add-on to Windows. My knowledge of Windows (and whatever third party utilities that are useful) is getting rustier all the time...

---

### Post by hyper_ch on 2007-10-05
I just think openssh-server and winscp is much simpler to setup than samba - if it's just file sharing....

---

### Post by Aamir Aziz on 2007-10-06
i've installed ssh but still i'm recieving the same error i.e

Documents and Settings\RANA>telnet 172.30.14.177
Connecting To 172.30.14.177...Could not open connection to the host, on port 23:
Connect failed

C:Documents and Settings\RANA>

i just want to access my pc from some other place to use GCC.

---

### Post by hyper_ch on 2007-10-07
```

sudo apt-get install openssh-server

```

And then you use WinSCP from [www.winscp.com](www.winscp.com) to connect to your linux box.

---

