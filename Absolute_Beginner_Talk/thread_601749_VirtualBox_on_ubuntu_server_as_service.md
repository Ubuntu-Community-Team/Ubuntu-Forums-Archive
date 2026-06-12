---
title: "VirtualBox on ubuntu server as service"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by micdhack on 2007-11-03
I want to create on my ubuntu desktop pc a virtualbox windows xp sp2 image...This is the easy part. The hard part i dont know is how can i take this virtualbox image and put it to run as a service on a ubuntu server without x(graphical enviroment).
Apparently copying all files from desktop to server is the first part..But with what command on terminal i can run the specific xp image? (in case you are wondering i will control this xp virtual machine with vnc)

---

### Post by schorsch on 2007-11-03
```
VBoxManage startvm *name_of_virtual_machine*
```
You can get *name_of_virtual_machine* via
```
VBoxManage list vms
```

---

### Post by schorsch on 2007-11-03
double post

---

### Post by micdhack on 2007-11-10
sorry for the delay...i had a lot work these days and i could test it.
As far as i can see this command is for windows but i have a linux OS. Which command should i run on linux?

---

### Post by schorsch on 2007-11-10
This command works on Ubuntu host with a Windows XP as guest to start the guest. I do not know it for Windows hosts as I do not have one :-)

---

### Post by micdhack on 2007-11-10
yes i can see also that it works..when i first tried it linux didnt recognize the command. This command is great it has all the command line management options for VirtualBox.

---

### Post by schorsch on 2007-11-10
Glad to hear that! Could you please mark your thread as solved as it may help others, too?

---

