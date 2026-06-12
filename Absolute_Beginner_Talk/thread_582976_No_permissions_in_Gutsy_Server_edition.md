---
title: "No permissions in Gutsy Server edition"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by kakka256 on 2007-10-20
Hi all.
I've been using ubuntu for a couple of months now, and i really like the desktop version. I figured i would try using the server edition aswell now that Gutsy is released. So just installed the server edition for the first time, on another pc.

It installed fine, but after the reboot i wanted to install some stuff and edit some files for which i needed to sudo.  The response was;

* "[username] not in the sudoers file. This incident will be reported."*  

wtf?

Since i dont have a root account and my auser is not allowed to sudo, i feel a bit stranded. Is there anything i can do?  Seems i need to have root privileges for just about anything that could help me right now...or?

Perhaps this is normal in the server edition, but i dont see anyone else asking about it :)

Any ideas?


Patrik

---

### Post by sas on 2007-10-20
That's not normal, are you in the 'admin' group? Pasting the output of 'groups' and your /etc/sudoers file may help.

If I'm right in assuming you have ubuntu server installed on a computer locally, just put the ubuntu live cd in, edit /etc/groups on your hard drive (not in the live cd session) making sure your username is at the end of the line starting with 'admin'

---

### Post by kakka256 on 2007-10-20
Thanks for the reply, sas.

I paniced when i couldnt solve the problem and decided to reinstall the server from scratch again (since i just did it three hours ago it wasnt a big deal), doing the exact same thing as last time except for not choosing the email-server this time (only dns and ssh).  After reboot sudo works just fine!

I have no idea what the problem was. perhaps i shouldnt have reinstalled and instead try to solve the problem a bit more... i might have stumbled upon some bug to report.

Ah well. Thanks anyways. Hope no one else has this problem :)

---

