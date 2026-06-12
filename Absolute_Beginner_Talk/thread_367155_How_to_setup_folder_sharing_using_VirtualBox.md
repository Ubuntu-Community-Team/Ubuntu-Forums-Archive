---
title: "How to setup folder sharing using VirtualBox?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by heinig on 2007-02-21
Does anyone know how to setup the folder sharing options using VirtualBox?
I'm using it to run Windows XP Professional as a guest in my Edgy box, but I'm not getting it right...
I followed the manual instructions (installed VirtualBox Guest Additions and ran ***VBoxManage sharedfolder add "Windows XP Professional" -name "VirtualFiles" -hostpath "C:\test"*** in a terminal but I get the following answer...

************

heinim@EdgyBox:~$ VBoxManage sharedfolder add "Windows XP Professional" -name "VirtualFiles" -hostpath "C:\test"

VirtualBox Command Line Management Interface Version 1.3.6
(C) 2005-2007 InnoTek Systemberatung GmbH
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath)) at line 5533!
[!] Primary RC  = 0x80070005
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070005
[!] Text        = The machine is not mutable
[!] Component   = Machine, Interface: IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}
[!] Callee      = IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}
[!] FAILED calling machine->SaveSettings() at line 5536!
[!] Primary RC  = 0x80070005
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070005
[!] Text        = The machine is not mutable
[!] Component   = Machine, Interface: IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}
[!] Callee      = IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}


*************

Any clue?

Thanks

---

### Post by Karl S. on 2007-02-22
Knowing nothing about computers, I had trouble with that method too. I ended up using Samba (instead?). Try the instructions [here.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

---

### Post by Pom2122 on 2007-02-22
> The machine is not mutable


That means that you have to run that command when no VMs are active or in a saved execution state. They should be shut down.

---

### Post by heinig on 2007-02-22
Finally I got it working!
I didn't realize that the VM has to be powered off to create one shared folder.(at least one that is non transient) 

I did as below:

**VBoxManager sharedfolder add "Windows XP Professional" -name "VirtualFiles" -hostpath "/home/heinim/Desktop/TesteVF"**

and in my guest VM I run the following...

**net use p: \\vboxsvr\VirtualFiles2** 

Now I'll be able to wipe-out my windows partition after a long time!
Thanks!

---

### Post by bob-aptllc on 2007-02-27
Where do you see the shared folder in your guest system?

---

### Post by heinig on 2007-02-27
I'm able to see my new network drive in My Computer.  

* There is a typo in my previous post 

Should be... 

VBoxManager sharefolder add "Windows XP Professional" -name "VirtualFiles" -hostpath "/home/heinim/Desktop/TesteVF"

net use p: \\vboxsvr\VirtualFiles

and not...

VBoxManager share**d**folder add "Windows XP Professional" -name "VirtualFiles" -hostpath "/home/heinim/Desktop/TesteVF"

net use p: \\vboxsvr\VirtualFiles**2 **

---

### Post by bob-aptllc on 2007-02-27
Thanks for your reply! I think you meant VBoxManage, rather than VBoxManage**r**.  ;-)

---

### Post by heinig on 2007-02-27
You're totally right...
That was another mistake.......haha.  I have to stop doing that.

---

### Post by Gary.M on 2007-06-08
> **heinig said:**
> Finally I got it working!
I didn't realize that the VM has to be powered off to create one shared folder.(at least one that is non transient) 


Whew!!! I just found this thread after several hours with this Machine is not mutable error!!! Now I have the shared folder working. Everyone take note, this should be in Virtualboxes helpfile and manual. I'd bet a few get caught with it!

---

### Post by gecko_gp on 2007-09-14
and is share**d**folder

and not

sharefolder

---

### Post by alonips on 2008-05-28
hello,
i'm having this error in the terminal:
 Syntax error: Not enough parameters
bernardo@bernardo-desktop:~$                    -hostpath "/home/bernardo/Music"
bash: -hostpath: command not found
bernardo@bernardo-desktop:~$ VBoxManage sharedfolder add "windowsxp" -name "Music" 
VirtualBox Command Line Management Interface Version 1.6.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Usage:

VBoxManage sharedfolder     add <vmname>|<uuid>
                            -name <name> -hostpath <hostpath>
                            [-transient] [-readonly]


Syntax error: Not enough parameters
bernardo@bernardo-desktop:~$                    -hostpath "/home/bernardo/Music"

what am i doing wrong?? Help me with this please.

---

### Post by hanniph on 2008-06-08
You have entered not a full command. Check your syntax. Make sure its:

```
VBoxManage sharedfolder add **virtualmachinename** -name "sharedfolder" -hostpath "/home/**username/foldertoshare**"
```

where
**virtualmachinename** is the name virtual machine you created.
**username** is your ubuntu home directory name. It's usually /home/your user name.
**foldertoshare** is the name of the folder you want to share.

---

### Post by AndrewTheArt on 2008-06-30
Note than an error like - 

```
andrew@andrew-laptop:/usr/bin$ /usr/bin/VBoxManage sharedfolder add "Windows XP" -name "ubuntu_share" -hostpath ~/VirtualBoxShare/
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath), fWritable) at line 7294!
[!] Primary RC  = E_ACCESSDENIED (0x80070005) - Access denied
[!] Full error info present: true , basic error info present: true 
[!] Result Code = E_ACCESSDENIED (0x80070005) - Access denied
[!] Text        = The machine is not mutable (state is 2)
[!] Component   = Machine, Interface: IMachine, {f95c0793-7737-49a1-85d9-6da81097173b}
[!] Callee      = IMachine, {f95c0793-7737-49a1-85d9-6da81097173b}
```

Might also arise if the virtual machine is in a "Saved" state. Make sure that your VM is both closed and that a saved state, if any, is discarded.

---

### Post by giacomop81 on 2008-07-16
I have the same problem, but i have a linux as guest system, how can i set the shared folder?
I just successfully configurated the shared folder to the "host side" with *VBoxManage sharedfolder...* command, but now I don't know how to mount the sahred folder in the "guest side"

Thanks.

---

### Post by Robocoastie on 2008-07-19
> **giacomop81 said:**
> I have the same problem, but i have a linux as guest system, how can i set the shared folder?
I just successfully configurated the shared folder to the "host side" with *VBoxManage sharedfolder...* command, but now I don't know how to mount the sahred folder in the "guest side"

Thanks.

Same question. The instructions in the user manual pdf hasn't helped me answer it yet.

Rob

edit/add: problem solved. See this: [http://forums.virtualbox.org/viewtopic.php?p=29389#29389](http://forums.virtualbox.org/viewtopic.php?p=29389#29389)

---

### Post by giacomop81 on 2008-07-24
You solved the problem wit the instruction on this post?
I don't yet...

I did it!
Thanks

---

