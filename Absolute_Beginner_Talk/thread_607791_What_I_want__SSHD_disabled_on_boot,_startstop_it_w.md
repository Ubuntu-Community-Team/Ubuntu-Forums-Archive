---
title: "What I want:  SSHD disabled on boot, start/stop it with script"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by evilregis on 2007-11-09
I want to configure my dad's computer to allow me to remote in when he has a problem.

However, I'm paranoid.  I don't like the idea of a port being open 24/7 (even if not the default port) for someone to get in and cause some damage.  As it is now, I've got it using port 8080 to handle SSH and I've set up hosts.allow/hosts.deny to only allow connections from my home and work IP addresses and it seems to be working.

Am I being too paranoid about it?  Is his system reasonably safe with the above measures?

If not, then what I would like to do is have SSHD stopped by default.  And when he requires assistance, he can launch a script that toggles SSHD.  If it's off, it turns it on.  If it's on, it turns it off.

Is that possible and does anyone have any helpful tips/URLs to get me started on such an endeavour?  Thanks!

---

### Post by kidders on 2007-11-10
> **evilregis said:**
> Am I being too paranoid about it?Yes hehe. Leaving an SSH server on is generally considered safe, provided your accounts are secure. Incidentally, port 8080 is an exceptionally bad choice. It's a common HTTP proxy port, so anything running on it is bound to attract a lot of malicious interest.

If you'd rather your SSH server didn't start on boot, take its startup script out of any runlevels you don't want it starting in. Even if you don't do that, you can still start & stop the service manually though.

---

### Post by steve.horsley on 2007-11-10
I too would be nervous about leaving an SSH server open all the time. There are lots of password guessing bots out there. However, hiding it at a high port (somewhere above 20000) will help. You could always look at enforcing the use of certificates - that's the safest thing to do. 

You can stop sshd from starting at boot by renaming the file /etc/rc2.d/S20ssh. Easiest is just putting an X at the front or something like that (files beginning with "S" are started at boot in the order of the following 2-digit number). Purists would argue that you should rename it to K80ssh instead. Look up sysv init for details.

Once you have renamed that link in rc2.d, you will have to start (and stop) it by hand wiht these two commands:
[B]sudo /etc/init.d/ssh start
sudo /etc/init.d/ssh stop[/B]

---

