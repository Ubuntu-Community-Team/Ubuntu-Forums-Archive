---
title: "Remote access to CVS repository made in Cervisia"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Golyadkin on 2007-05-01
Hi everyone.

I am writing a thesis in LaTeX and keep my source files in a CVS repository I created in Cervisia. This works great but now I installed Ubuntu on my other computer as well and I would love to access the repository over the network. I know I can use server: for this, but it can't access the repository.
I am running Ubuntu 7.04 Feisty Fawn (GNOME) on both computers.

Is there an easy way to make this repository accessible to both machine?

Any help would be greatly appreciated!

Thanks in advance,

Golyadkin

---

### Post by tbg58 on 2007-05-01
Access to this repository is via the ssh port.  By default the sshd is not installed on Ubuntu, but it's easy to install.  You can do either of the following:
1.  At a terminal shell, type sudo apt-get install ssh

2.  Go to System, Administration, Synaptic Package Manager, and select SSH as the package to install. 

The quick way to check to see if you have sshd installed and running is to go to your other Ubuntu box and type 
ssh (otherhostname) in a terminal.  The first time you ssh in, you will be asked to cache a key file, then you should be set.

Hope this helps!
Good luck.
For further Cervisia issues, you may want to check their wiki, documentation and discussion lists.

---

### Post by Golyadkin on 2007-05-01
Hello tbg58.

Do you mean that I can access this repository by logging in with SSH? I don't want to work on the files on the other computer directly, I want to be able to connect to to CVSD server from another machine, using Cervisia as a client there as well. 
Is this possible with SSH ? I have sshd installed.

Thank you, Golyadkin.

---

