---
title: "2 ssh servers behind a router"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-07-11
i have 2 linux computers that are on the same router. I'd like to be able to ssh to each computer individually from a remote location. so i set up ssh servers on each, and set up port forwarding as such:

router has an IP, and registered that IP at dyndns
my laptop has an ssh server listening on port 22 (standard)
my desktop has an ssh server listening on port 2200 (not-so-standard)

i can connect to one. if i connect to my laptop first, then disconnect. it wont let me ssh to the desktop and says i may be subject to a man-in-the-middle attack (obviously not what's really going on). if i delete my .ssh/known-hosts file, i can then connect to the desktop, but now i cant connect to the laptop after that for the same reason as before.

so how do i get around this error?

thanks in advance.

---

### Post by dannyboy79 on 2007-07-11
first of all, you don't need to connect from the other internal machine from the local machine (meaning you don't need to actually log out of your first ssh session, just so you can log into the other machine), just ssh over from the first machine to the second using 
ssh username@ip
from the bash prompt of the first machine.

as for it saying you may be subject to man in the middle attack, well since you know it's your machine, then just accept it and from then on, you won't recieve that warning. if for some reason you do want to be able to connect to both machines externally, then just accept the warning. otherwise look into the ssh client and how it accepts keys or whatever they are called.

I suppose it's possible that you modified the default /etc/ssh/sshd_config and changed these things

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes


but I didn't and I have no problem when I login via ssh from a new host. so check that file with sudo privleges and see if your settigs are different, and change them like mine. I DO use public/private key paris for authentification so I am not concerned with RhostsRSAAuthentification.
if you're saying that the client WON'T let you connect to it, than you need to look into the preferences of for that client. I know in Putty for windows, I just hit accept and it works. good luck

---

