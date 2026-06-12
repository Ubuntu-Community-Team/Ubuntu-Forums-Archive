---
title: "SSH + Nautilus + Sudo"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by iluminate on 2006-06-03
Hi all,

I have a problem. I am using now Nautilus to access a remote ubuntu box and everything is going well, until I need to use the SUDO command.
How do I i do it via nautilus?
The thing is that I need to copy some files in a folder, which I as a user do not have permission to do, unless I sudo.

So my question  - Is this possible at all?

Or do I need to login via the terminal, change the permissions of the systemfolder and then use nautilus?

Take care ya all!

---

### Post by steve.horsley on 2006-06-03
I would advise that you use ssh login and sudo commands to copy files to your home folder on the remote machine, and then use ssh to transfer files from your remote home folder, and use the ssh login and sudo commands to transfer. Delete the copies in your home folder when done. 

My main reason for saying this is that I don't like the idea of meddling witht  the proper file permissions.

---

### Post by Sirkent on 2006-06-03
As steve.horsely has said, meddling with file permissions isn't always a good thing, so ssh is certainly the best option.

As far as I know there's no wait to alter permissions from Nautilus unless you're connecting as a user which already has owner priveledges on those directories/files. If you're trying to do anything other than alter permissions with sudo, then you certainly can't do that with Nautilus.

---

### Post by iluminate on 2006-06-03
Hi and thank you for your reply.

But wouldn't be great to be able to use the sudo command in Nautilus?
Now I like have to do this 2 step thing, first copy the files to my homefolder.
Then login via terminal SSH, copy files to its right location.
Should it be really like this?

---

### Post by Sirkent on 2006-06-03
Well, Nautilus is meant to be a file manager, but when it comes to performing commands on a remote system - that's what ssh is for. You could easily do it all through ssh - change the permissions, copy the files, perform a command with sudo, etc.

---

### Post by bluefrog on 2006-06-04
install openssh-server on the computer you want to access.
then on client computer, places > connect to server > ssh. Fill in necessary info. click ok. 
open the newly created icon on your desktop, fill in necessary password (accpet the warning as well before)
you're done. you have nautilus brwosing via ssh

James

---

### Post by Tortanick on 2006-06-04
I'd SSH into the other computers terminal, then use sudo nautilus.

---

### Post by steve.horsley on 2006-06-04
You could:
install an SSH server on your local machine as well
use ssh -X to connect to the remote machine
run sudo nautilus on the remote machine to get a root nautilus running
use that nautilus to ssh back to your machine and copy the files straight back

or just enable root ssh login on the remote machine by setting a valid root password, and use your local nautilus to connect as root. This is the easiest way, but leaving a root-connectable ssh server is just asking to be hacked.

---

