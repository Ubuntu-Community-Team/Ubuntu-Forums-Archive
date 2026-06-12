---
title: "Want to share files between Ubuntu, XP"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by jwharmon on 2006-09-02
Complete newbie to Ubuntu here, though I have mostly been able to get it to do what I want it to do since I installed it about a month ago on an old laptop. But I've run into some problem on something that has confounded me before: networking computers.

What I want to do is use a crossover cable to transfer files between my Ubuntu computer and my Windows XP computer. This won't be something that's plugged in all the time, just when I need to transfer things. I've spent a couple of days looking through what's been posted here and learned about the existence of Samba. However, I've had very little progress.

I was able to get the Windows machine to show up in the "Network Servers" listing, but clicking on it gives an error saying "couldn't display all the contents." I have shared directories on both machines, but the XP one isn't seeing the Ubuntu one at all.

I've created a new smb.conf as described in the "setup Samba peer-to-peer with Windows" post, but it didn't seem to do anything. I'm not even sure if that's what I'm supposed to be doing. 

Any help anyone can give me on this would be greatly appreciated!

---

### Post by jorn on 2006-09-02
Using Samba it is possible to se files both ways between xp and ubuntu.
You might try this link:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://www.ubuntuforums.org/showthread.php?t=236575&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=236575&highlight=samba)
Or browse for other Samba-setups, there are a few of them.

---

### Post by David Corrales on 2006-09-02
You probably have a firewall active in your Windows box. Disable it and try again.

---

### Post by Toxicity999 on 2006-09-02
Disabling a firewall for one app isn't always the best of solutions ;) Just allow port access for samba or whatever you choose to use. Of course deactivating a firewall always works but if your paranoid not the best option.

---

### Post by David Corrales on 2006-09-02
I suggested disabling the firewall for troubleshooting. But Toxicity999's right, once you diagnose the problem you should only open the necessary ports for SMB.

---

### Post by Toxicity999 on 2006-09-02
right my usual method for things that don't seem to work of that nature.

-Disable the firewall.
-Check if it works then.
-Re-enable the firewall and track down the ports the prog. uses.

Many might disagree but it works!

---

### Post by David Corrales on 2006-09-02
> **Toxicity999 said:**
> right my usual method for things that don't seem to work of that nature.

-Disable the firewall.
-Check if it works then.
-Re-enable the firewall and track down the ports the prog. uses.

Many might disagree but it works!

That's a fine way to do it if you can isolate the machines having problems from potentially dangerous hosts.

---

### Post by jwharmon on 2006-09-03
Turning the firewall off did nothing that I can tell. Ubuntu can still see the Windows network put can't get to any directories, and Windows still can't see the Ubuntu computer.

Here's a few things I didn't mention that might be playing a part in this.
1. Both of these computers have wireless cards that are accessing the Internet.
2. Whenever Windows tries to resolve the connection w/ the Ubuntu machine through the crossover cable, I get the "Limited or no connectivity" message. Is there a similar message I should be getting on the Ubuntu machine? I've no idea where to look.

I admit to confusion on the "Setup Samba peer-to-peer with Windows" instructions. When it talks about setting up users and passwords, do I need to use my Windows username in there somewhere? Do I need to set up the user name for my Ubuntu machine as well?

---

### Post by Garyu on 2006-09-03
a good way of connecting machines is using ssh. it is a secure way of sharing files and even using terminal commands on your remote machine.

[http://www.bitvise.com/download-area.html](http://www.bitvise.com/download-area.html)
tunnelier is an ssh client for windows. winsshd is a daemon/server.

[http://sshwindows.sourceforge.net/download/](http://sshwindows.sourceforge.net/download/)
openssh client and sources for windows machines can be downloaded from here.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
putty is a telnet/ssh client for many platforms including windows.

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)
winscp is scp (secure copy over ssh) for windows.

And finally, for your Ubuntu system:
[http://www.ubuntuforums.org/showthread.php?t=103860&highlight=howto+share+ssh](http://www.ubuntuforums.org/showthread.php?t=103860&highlight=howto+share+ssh)
howto mount ssh shares.

[http://easylinux.info/wiki/Ubuntu#SSH_Server](http://easylinux.info/wiki/Ubuntu#SSH_Server)
some info on how to use ssh in a terminal.

to use nautilus, simply click locations->connect to server in the menu and enter ssh://mycomputerip/sharedfolder


of course, you don't need all of that, the links are just to give you some tips. personally, i thought ssh seemed difficult at first so i tried about everything else first, but finally had to turn to ssh and realized that it's just great.

if you don't want to learn how to use the good stuff though, and want to keep up the old windows way of working, try vsftp and use ftp clients to connect the two computers. i'm sure you can find lots of ftp servers for windows. here is a howto for vsftpd:
[http://www.ubuntuforums.org/showthread.php?t=91887&highlight=vsftp](http://www.ubuntuforums.org/showthread.php?t=91887&highlight=vsftp)

---

