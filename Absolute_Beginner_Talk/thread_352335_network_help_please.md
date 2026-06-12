---
title: "network help please"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-02-03
I have some exp. with linux but I can't figure out how to set-up my home network.I have 2 computers with ubuntu and 1 with kubuntu.They are all plugged into the same router and they can't see each other or share files.Any help would be greatly appreicated :confused:

---

### Post by moshuptrail on 2007-02-03
File sharing.  Well....

It doesn't just happen automatically.  There are several ways to do it.  I think most people use NFS.  With NFS you actually "mount" the remote directories as if they were part of the local filesystem.  I've never done that. (I probably should)  I've always used samba because I needed to share with windows PCs around the house.  Samba is the other common file sharing tool - it emulates windows file sharing but is a bitch to get it set up right.

Suggestion: Do some searches, here and in the wiki on NFS and file sharing.  The setup will take a little work, but when done, Linux is pretty nice to share files with.

p.s. the ubuntu/kubuntu/xubuntu won't make a difference.

---

### Post by Jussi Kukkonen on 2007-02-03
Please describe the situation in more detail:
* Does either of computers have a working internet connection? Can you ping the router from the machines?
* What exactly do you mean when you say they don't see each other (have your tried e.g. ping)? 

(in case this was foreign terminology to you: pinging means running e.g. "*ping 192.168.0.1*" in a terminal, the number in the example is the IP address of  my router).

---

### Post by tocleora on 2007-02-03
It's been a while, but I believe this is what I did to "share" a folder between my two linux servers:

[http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/)

And then there was a way to put that in fstab so it would automatically share on boot. I'm not at the right computer to post that information but I'll look and repost if no one else does. This thread might help:

[http://ubuntuforums.org/showthread.php?t=275856](http://ubuntuforums.org/showthread.php?t=275856)

---

### Post by Jussi Kukkonen on 2007-02-04
copy-pasting from TImmys private message (hope you don't mind):
> They all have a internet connection.They can ping each other and the router they just can't share any files with each other.I just don't understand why.If they can see each other and ping to. then why can't I share with each other.

Ok, cool. Can you tell what you have done to  enable file sharing?

Btw, what tocleora is suggesting works, but is definitely not the most popular method -- NFS or Samba are. I believe you can find howtos for both in wiki.ubuntu.com or [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) . Like moshuptrail said, Samba is useful if you have Windows machines. Otherwise I definitely recommend NFS.

---

### Post by tocleora on 2007-02-04
> **Jussi Kukkonen said:**
> Btw, what tocleora is suggesting works, but is definitely not the most popular method -- NFS or Samba are.

Yeah I didn't want to use Samba because I knew it's primary purpose was Windows compatibility, I knew there had to be something just for linux to linux sharing, but my searches for that phrase only resulted in the method I responded with.  I too will check out NFS now.

---

### Post by Moulton on 2007-02-04
If you are using DHCP from the router for each machine to obtain an IP address, then it might be hard to use NFS, because NFS generally expects the server machine to have a fixed IP that is defined in the /etc/hosts file and/or a DNS (domain name server).  To use NFS, you should plan to assign fixed IP addresses to each machine within the IP range that your router recognizes, and place entries in the /etc/hosts files on each machine.

Over the years, NFS has increased the security requirements, to the point where you have to carefully set everything up so that each machine can authenticate every client and server they connect to.  This is because NFS doesn't authenticate with individual userid and password the way SMB/CIFS does.

---

