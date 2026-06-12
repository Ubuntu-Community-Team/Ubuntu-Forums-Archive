---
title: "sshd problems"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by TonyLB on 2008-03-27
Not sure if this is the right forum, but here goes.

The startup script should be starting sshd but it doesn't, with no error messages.  I tried to start it from the command line /usr/sbin/sshd and got the error message that /var/run/sshd was missing, so I created that directory (using sudo).  I could then start sshd from the command line.  On reboot, the directory had gone, so I needed to do it again.

With or without the directory, /etc/init.d/ssh start/restart both fail to work, with a comment about sshd_config_not_to_be_run, which is present.

I'm completely confused over what is going on.  I've not had this problem with other 'nix variants and I don't know much about scripting.

Oh, I'm using XUbuntu 7.10

Tony

---

### Post by Thanoulis on 2008-03-27
Are you sure you installed the ssh server?
I use the openssh-server package and works like a charm for me...

---

### Post by TonyLB on 2008-03-27
Solved it!

I masked openssh-server for complete removal, and anything else connected with ssh apart from openssh-client.  Then reinstalled the server and it all worked.

Originally there was a small file /etc/ssh/sshd_not_to_be_run which said in it DO NOT REMOVE THIS FILE.  Turned out it was lsh-server which had been installed and which stops sshd running by putting the file there.  Once lsh-server had been removed, the file went away and so did the problem.

Tony

---

