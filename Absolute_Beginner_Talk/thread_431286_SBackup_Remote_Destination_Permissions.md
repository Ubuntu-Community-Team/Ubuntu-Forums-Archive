---
title: "SBackup Remote Destination Permissions"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by vba_djs on 2007-05-02
I am trying to configure the remote destination of SBackup using SSH with the following:

ssh://loginname:loginpassword@ipaddress/destination/

When I click the Test button, I receive the following message:
"The selected destination is not writtable with current permissions."

The permissions on destination are:
drwxrwxrwx root root

Both boxes are behind my firewall and both are running Ubuntu server 6.06.

Using loginname and loginpassword I am able to connect from the source server to the destination server via SSH in a terminal window and write files with the 'touch' command.

So it appears that SSH is working and that the permissions are properly set.

Any suggestions??

Thanks.

---

### Post by ktulu1115 on 2007-05-29
Wish I had an answer, I'm suffering from the same problem myself.  Became an issue when I upgraded my remote (server) to Feisty.

Permissions are fine, I can login directly with "ssh backup@server" with no problem.  Can also change to the specified directory and can 'touch' files.

---

### Post by ktulu1115 on 2007-05-29
SOLVED:

Solution here - [http://ubuntuforums.org/showthread.php?t=393235](http://ubuntuforums.org/showthread.php?t=393235)

Just do a 'sudo rm /root/.ssh/known_hosts' on the source machine, then the "test" button will report success.

---

### Post by vba_djs on 2007-05-30
Thanks for your reply.

However, the known hosts did not exist on my system.

I un-installed and re-installed SBackup, without any more success.

---

