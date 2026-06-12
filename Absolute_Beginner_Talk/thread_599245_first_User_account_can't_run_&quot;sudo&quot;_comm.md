---
title: "first User account can't run &quot;sudo&quot; commands"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Tom_Thumb on 2007-11-01
Hi,

I'm a complete noob with Ubuntu and Linux in general and have just installed Ubuntu 7.10 Server edition. I got an issue though, which is seriously holding me back. It appears that my account (created during the install) wasn't added into the "sudoers" file. When I try to run the command "sudo apt-get install ubuntu-desktop" and enter my Password, I get the error "USERNAME is not in the sudoers file. This incident will be reported." 
So now I can't install the GUI or any other packages for that matter.
Any suggestions as to how to either start a root user session to edit the "sudoers" file so I can add my account into the admin Group, or some other way to accomplish something similar e.g add another user with "sudo" rights?
Anything you could tell me would be appreciated.

---

### Post by damotor on 2007-11-01
Use your live cd, mount the partition where ubuntu is installed and modify the /etc/sudoers file.

---

