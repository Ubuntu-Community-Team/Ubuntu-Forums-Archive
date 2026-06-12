---
title: "Just another Remote Desktop question"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by jasperstroomer on 2006-11-19
Well hello all,

Last week I decided to transform my old pc into a server. Ofcourse I could just install M$ Server 2003, downloaded from the internet, but that would be illegal, and we don't want't that... do we...

So, I decided to try Ubuntu for a change. The installation went fine. I love the simplicity of it all. After a little bit of searching on the internet I also got Apache, Mysql and PHP to work just fine. The only remaining problem for now is the remote access.

I've been searching on this forum for solutions, and got VNC to work fine, the only problem was that it forgot my password after each reboot, but I saw that was a known bug.

The problem i'm having now, is that i cannot connect to the server after a reboot. The VNC will only allow me to connect after i have logged in at the local machine. 

Is there a solution for this? I would like to be able to log into my server from a remote pc, even after a reboot.

P.S, A remote desktop solution would be great, but if there is some other solution that just gives me a terminal..... fine.

Thanks,
Jasper

---

### Post by bodhi.zazen on 2006-11-19
I believe [ssh](http://www.openssh.com/) is what you are asking for

If you are on a windows box try [putty](putty).

[How to](https://help.ubuntu.com/community/SSHHowto)

Putty is a ssh client for windows....

---

### Post by jasperstroomer on 2006-11-19
Hey thanks! It works, and a lot easier than I thought it would :-)

Can someone please confirm if my thinking is right when i say.... When the bug in Vino VNC is fixed ( so it does not forget the VNC password after each reboot ), and I have logged in to my server using putty, I can use a VNC client to access my desktop? ( because VNC only does work when a local user has logged in ). Or is there a way to show the boot up the desktop through putty?

Again, thanks for the fast response,
Jasper

---

### Post by bodhi.zazen on 2006-11-19
> **jasperstroomer said:**
> Hey thanks! It works, and a lot easier than I thought it would :-)

Can someone please confirm if my thinking is right when i say.... When the bug in Vino VNC is fixed ( so it does not forget the VNC password after each reboot ), and I have logged in to my server using putty, I can use a VNC client to access my desktop? ( because VNC only does work when a local user has logged in ). Or is there a way to show the boot up the desktop through putty?

Again, thanks for the fast response,
Jasper

I assume you are running on windows.

Yes, you can forward X and run a desktop on windows (or linux for that matter...ssh -X).

On the windows side you need a X server. I have used [Cygwin](http://www.cygwin.com/). IMO it was faster then vpn.

You can also try [openvpn](http://openvpn.net/howto.html). (I do not know what vpn you are using, but if you aer open vpn, there are others.. [tight vnc](http://www.tightvnc.com/) also works).

---

### Post by tbresson on 2006-11-20
I have problems with my VNC too. It works fine until reboot, then I need to set the password again.

This wasn't so in Ubuntu 6.06 - it's a new feature in 6.10 I guess, still working on how to fix it.

---

