---
title: "Is SSH redundant when using OpenVPN?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Cadmus on 2007-12-06
I've got OpenVPN set up and happily running. I know the canonical way to access another machine is using ssh in order to stop people looking at your network geting a hold of passwords and the like. My questions are:

[LIST]
[*]Is ssh necessary with a vpn?
[*]Does it add more noticably more overhead or reduce bandwidth?
[*]Is telnet ok when the infrastructure is trusted?
[*]Because telnet is used so little (from what I can see) is it a thornier to use than ssh?
[/LIST]

Apologies if it's not the best forum, still getting to grips with the layout here.

---

### Post by rev.tig on 2007-12-06
* Is ssh necessary with a vpn?
It depends on what you class as necessary,  I would always use ssh even on a "trusted" network as you can never be sure it has been compromised.  Also ssh gives you so much more!

Did you know you can use SSH to transfer files using sftp (secure ftp)
Did you know you can use SSH to tunnel traffic (ssh tunnels)?
... and lots more :) 

I would not run a telnet server as it is just asking for trouble,  telnet is old technology there is no reasonable argument for running it on a modern operating systerm for accessing machines.

    * Does it add more noticably more overhead or reduce bandwidth?
Although there is a small overhead ssh traffic is compressed so it is very lightweight.

    * Is telnet ok when the infrastructure is trusted?
Personally I would never steer anyone near telnet unless it is totally unavoidable,  there is no point.  Telnet is vulnerable to man in the middle attacks for example if someone did get onto your trusted network they could snoop your traffic and you would never know.   They cannot do this with SSH.

    * Because telnet is used so little (from what I can see) is it a thornier to use than ssh?
It is outdated now,  ssh was designed to solve all of the downsides of telnet,  the lack of encryption and features.    Telnet really is a technology that is still around in legacy form only no-one should be considering putting in a new telnet installation  in this day and age.

Telnet,  just say no :)

---

### Post by Cadmus on 2007-12-10
Thank-you for the thorough reply, I'm now getting my hands dirty using cygwin from work to control my media centre.

---

### Post by hyper_ch on 2007-12-10
you can even mounte remote filesystems with sshfs ;)

---

