---
title: "How LTSP client works ?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by ederlezi on 2007-10-06
Hi, 

I am trying to understand my LTSP problem. The problem is the matter that I:

- installed UBUNTU 7.04
- installed LTPS as shown in [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)
- i created user "tester" and set the password "tester" to it

When I booted LTSP client (I mean PC computer with no hard disk ) I had no problem with booting ( probably DHCPD and TFTP work fine ), but I couldn't have logged using any user ( especially "tester" which was created 10 miuntes before I run my first LTSP client ). Login was incorrect. I checked auth.log and I saw that the autentication was alright. 

Ok , on LTSP server I put

chroot /opt/ltsp/i386

I added user "misio" and created password for it.
I rebooted LTSP client ( pc computer ) and wanted to log as "misio". Logging was impossible via graphical screen , however when I pressed "Ctrl + Alt + F1" I could have logged into shell. 

Is my LTSP server working fine and I should configure somehow LTSP environement or my LTSP definetely does not work fine?

---

### Post by SpiritIsReality on 2007-11-01
howdy
could you have a look at this and see if it works?
> This workstation isn't authorized to connect to server error message on client, please run commands sudo ltsp-update-sshkeys and sudo ltsp-update-image (in this order) reference:[WWW] [https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296) 
[https://help.ubuntu.com/community/LTSPServerSetup](https://help.ubuntu.com/community/LTSPServerSetup)
hopefully that gets you logged in.
now correct me if I'm wrong, but the way I glean it, the chroot environment is used to boot the client, and then it logs into the server /home environment. So the users are to be created on the server environment, not the chroot /opt/ltsp/i386 environment.
System -> Admin -> Users and Groups -> +Add User. The packages (programs) available to the client are added to the server environment, not the chroot client environment. The chroot is updated and upgraded to keep the mini environment updated 
for the boot of the clients.

others
[http://www.uluga.ubuntuforums.org/showthread.php?t=592873](http://www.uluga.ubuntuforums.org/showthread.php?t=592873)
[http://ubuntuforums.org/showthread.php?t=484846&page=7#post3726136](http://ubuntuforums.org/showthread.php?t=484846&page=7#post3726136)
[http://linuxagora.com/vbforum/showthread.php?t=333](http://linuxagora.com/vbforum/showthread.php?t=333)
the motherload !!!
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Debian](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Debian)

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[http://www.edubuntu.org/](http://www.edubuntu.org/)
[http://www.edubuntu.org/Documentation](http://www.edubuntu.org/Documentation)
[http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-theory.html](http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-theory.html)
trails

---

