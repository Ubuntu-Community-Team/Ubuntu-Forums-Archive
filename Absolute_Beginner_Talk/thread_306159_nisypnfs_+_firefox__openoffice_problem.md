---
title: "nis/yp/nfs + firefox / openoffice problem"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by vtripolitakis on 2006-11-24
Hello,

I just installed ubuntu 6.10 a couple of days ago on a computer.

This computer is on a lab and uses nis/yp and mounts the home directories using NFS (I've installed nfs-client). 

I can properly login and access various user account files.

I changed group permissions to add audio/cdrom/scanner etc support to nis user accounts.

Firefox 2.0 and Openoffice 2.0 **run properly on local accounts**.

On the other hand they **don't start** on nis accounts. I deleted all relevant application directories (e.g. .mozilla etc), but the problem persists. 

Any suggestions will be welcome.

Thank you in advance

Evangelos Tripolitakis
Electronics & Computer Engineer, MSc

---

### Post by obiyoda on 2006-11-29
I am having the same problem as you. Looking at the bugs there seem to be quite a few concerning edgy and nfs. This was all working fine under 6.01 for me. May down grade back to 6.01 to get this working again. Don't want to do that So I will keep poking around and see what I can find out. At least I'm not the only one experiencing this. :)

 
[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/71212]("https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/71212")
The last post here may contain a solution. But I am pretty new to this Linux thing and haven't compiled a kernel yet.

---

### Post by obiyoda on 2006-11-30
I recompiled my kernel on the nfs-server using this howto [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")
It solved my problem of users not being able to use openoffice or firefox.

---

### Post by vtripolitakis on 2006-12-06
Hi,

I just needed to restart my nfs-server and everything worked as it should.

---

### Post by Steven Heuser on 2007-04-03
All,
    I'm seeing this same behavior on three boxes running Fiesty. All the NIS validated accounts won't let Firefox run but local accounts will. My server is running Edgy with NFS, NIS and Samba. I've tried rebooting clients and server and wiping out the .mozilla directory in a user's home all with no success. I have not tried rebulding the kernel on the server yet (not brave enough).

---

### Post by Steven Heuser on 2007-04-04
Hello again,
    I followed obiyoda's suggestion and re-compiled the Kernel on my server. This appeared to fix the problem as well. As far as building the kernel with VERY few config mods, I just followed the simple steps located on the Ubuntu wiki site at 
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
I then downloaded all the appropriate stuff and followed the "Old-Fashioned" Debian Way without a hitch! Hope this helps anyone.
-Steve

---

### Post by Steven Heuser on 2007-04-07
I'll take back what I said earlier. Rebuilding the kernel on my server helped for a day but then my clients started acting up again. I was too chicken to try a newer kernel so I just rebuilt 2.6.17-11. Now the clients sometimes let Firefox run and sometimes not. Here is a related thread I found about this issue. [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/73457](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/73457)
However it looks like it was resolved (or the problem just went away)
For now my fix is to punt Firefox and use Epiphany. I believe it is a nasty NFS problem that seems to have reared its ugly head in Edgy and later Ubuntu. See this link for more info [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62308)
-Steve

---

### Post by Steven Heuser on 2007-04-13
Okay.... looks like I find the patch for the problem. Looking at the links in my last post I found an obscure option to set in the /etc/exports file.  On my drive that I export I added the option no_subtree_check. This seems to have done the trick and if someone wants all the gory details as to why this works check the links in my last message.
-Steve

---

### Post by Despot on 2007-04-21
Hmm. I'm having the same problem (except I'm not mounting the entire home directory, just Mozilla's stuff) on Feisty release. Problem is, I can't add that option to my server because it's an OpenBSD-based system with an NFS server version that does not appear to support the 'no_subtree_check' option...

Any other ideas?

---

### Post by Despot on 2007-04-21
Nevermind, I got it. In troubleshooting another problem, I ran across this in /var/log/message:

[INDENT]lockd: couldn't create RPC handle for slave1[/INDENT]

Firing up lockd on my NFS server made it all better.

---

### Post by lordmundi on 2007-05-01
> **Steven Heuser said:**
> All,
    I'm seeing this same behavior on three boxes running Fiesty. All the NIS validated accounts won't let Firefox run but local accounts will. My server is running Edgy with NFS, NIS and Samba. I've tried rebooting clients and server and wiping out the .mozilla directory in a user's home all with no success. I have not tried rebulding the kernel on the server yet (not brave enough).

I am seeing the exact same thing as well.  Furthermore, things were running well until I updated one of the machines to Feisty.  Is something in Feisty killing something on the server side?  I get the lockd errors and I cannot figure out how to fix this.

---

### Post by lordmundi on 2007-05-01
ok nevermind... i replied without looking at page 2!!! doh!

restarting the nfslock service on the server seemed to do the trick... although i have no idea why this died.  Earlier this week I had to restart named as well... hmm...

---

### Post by tvreeland on 2007-09-04
Just to add a comment, much to late to help you all...

I had the same problems and couldn't get access to the BSD server.  So, I simply did the NFS mount with the 'nolock' option and everything was better!

Hope that helps somebody else coming to this later...

---

