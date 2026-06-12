---
title: "Samba on Xubuntu"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by bdemers on 2008-02-10
Just looked at suggested threads, didn't help.  

apt-get install samba   this is the command line I entered.

I have a Windows Xp  workgroup called "workgroup", dhcp, local windows firewall turned off.

I set up a share of my home dir on xubuntu.

My windows machine sees my xubuntu machine, but won't logon.  I am using my username without any domain name and my password with correct case.  Network , General Tab has blank for domain name, tried adding "workgroup" and logon still failed.  I am sitting behind IPCop, but don't see anything with that to cause this.  In fact I can logon,  file transfer from same  Xp machine to another Ubuntu machine, but that's using scp3 and ssh.

In my opinion, I need some help.

Second thing, using xubuntu how do I see the samba shares? Now that's a real head scratcher!

Thanks for your help and patience.

---

### Post by spiderbatdad on 2008-02-10
you should have a folder called Shared Folders under System>>Administration, but getting smb.conf set up with correct permissions is key.

---

### Post by milesstandish on 2008-02-12
If you're using Windows Vista, there are some settings you will need to change there first. I believe you can make the proper changes by running ipsec from the run command. I can't remember off-hand what changes you make, but Google "samba vista" and you should find plenty. Its very easy to do.

---

