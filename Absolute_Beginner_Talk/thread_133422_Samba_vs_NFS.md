---
title: "Samba vs NFS"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-02-20
Hi all,
I have two ubuntu boxes, one still keeping an occasionally used XP dual boot (2HDD), but most of the time its just ubuntu to ubuntu.  Sometimes, I may need to move a file from the xp disk to the ubuntu.  Plus there's a printer on the dual boot box, which I need toshare with the other ubuntu box.  And I want to share folders on the dual boot ubuntu box.
Should I use NFS or Samba?
Can I write from the XP disk straight to the Ubuntu disk (I can't see the disk yet), or is it better (if more longwinded to go through sambas and stick it on box 2 and from there to the shared folder on box 1 ubuntu?

Plus, as an XP migrant, and a linux newbie, Samba seems easier to set up.  I looked alot at this on the Wiki: [https://wiki.ubuntu.com/SettingUpNFSHowTo](https://wiki.ubuntu.com/SettingUpNFSHowTo)
but it all seems a little complicated (to me at least) and to involve internet security issues (not to mention dealing with hoary, and disagreeing with other threads!).  Is there any reason not to Samba two linux boxes, and will it printer share OK?

Thanks

---

### Post by Robgould on 2006-02-20
I use samba and it is very easy.  I use it to bridge my xp box and ubuntu laptop over my wireless network, so I know this will work well when used that way.  I don't know what issues there may be with samba and two linux boxes.

---

### Post by damianubuntu on 2006-02-20
Hey Rob,
Didn't I read in one of the threads that I've been ploughing through, that you've got an NFS server client setup too?
I deccided to go for NFS in the end, and access the XP stuff through mounting the drive to Ubuntu.
Problem is, I can't seem to find a reliable and complete guide to setting up the NFS server, and I suspect that by half reading advanced stuff that is half relevant, I'm losing myself completely.  So far I don't even know if I've got the right stuff even installed, I suspect not.  So I thought I'd try and get right back to the beginning.  Any pointers as to what I shoudl have, and some relable steps through, that don't assume too much prior knowledge?

For what its worth rpcinfo tells me that I have portmapper and status, but thats all.  On of hte problems I have is that the various articles referr to version 2 or 3 of NFS and most of them seem to talk about older kernels, or ubuntus, plus whilst I don't mind using terminal, it seems a good idea to use the GUI that badger provides, and that again conflicts with the articles.

Thanks for your help
D

---

### Post by carlosqueso on 2006-02-20
[https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29) may be a lot easier.   It's command line, but I got everything working through it and it's a lot simpler than the other howto.

---

### Post by damianubuntu on 2006-02-20
Hi Carlos,
yes I started with that one ;-) and when I couldn't get it to work, went on through the one bu Matthew Caron at the bottom, and now I'm working on this one:
[http://www.linux.org/docs/ldp/howto/NFS-HOWTO/server.html](http://www.linux.org/docs/ldp/howto/NFS-HOWTO/server.html)
I seem to be able to get the server running right now, with rpcinfo showing the right range of stuff (I think), but rpcinfo *server* on the client just times out with can't contact portmapper:RPC:remote system error.

Just going back over the host/allow/deny files now

Cheers for your input
D.

edit: should that be times out or timeouts?;-)

---

### Post by damianubuntu on 2006-02-20
BLOODY FIREWALL!!!!:twisted: :twisted: :twisted: 

nuff said

---

