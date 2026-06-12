---
title: "vmware install?  (not)"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by leetj on 2007-07-07
i started to use linux 5 hours ago  , i am trying to install vmware server on ubuntu feisty , it works ok untill i have the multiple choices about where to install certain elements of the programme, they all seem to work then it asks :

In which directory do you want to install the documentation files? 
[/home/lee/doc/vmware] 

The path "/home/lee/doc/vmware" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want? 
[yes] 

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.


it asked me a series of questions before this of which i had no problems 
pleese  can you help me out 
all responses would be most welcome indeed
thank you 
lee

---

### Post by KyleBrandt on 2007-07-07
When you run the install script, are you running it with root privilages? If not, you would do so by using "sudo command" .  So in the case of vmware desktop I think it would be "sudo ./vmware-install.pl"

---

### Post by MyR on 2007-07-07
If you don't already have VMs you're using, I recommend virtualbox instead of vmware. It's a LOT faster in my experience.

---

