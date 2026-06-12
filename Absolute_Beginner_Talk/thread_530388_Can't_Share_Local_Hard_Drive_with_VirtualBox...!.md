---
title: "Can't Share Local Hard Drive with VirtualBox...!"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by milinda on 2007-08-20
I used Ubuntu 7.04 feisty fawn and used VirtualBox  to use a guest Operating system (WindowsXP) . N Used following tutorial to configure most of the things in my guest operating system. I tried to share my local system folder with the guest operating system as in the tutorial but it gives following error msg. 
============================================================
**root@KILLER-M:/home/milinda#** VBoxManage sharedfolder add "winXP" -name driverD -hostpath "/home/milinda/"

VirtualBox Command Line Management Interface Version 1.4.0
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] FAILED calling aVirtualBox->FindMachine(Bstr(argv[1]), machine.asOutParam()) at line 5707!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070057
[!] Text        = Could not find a registered machine named 'winXP'
[!] Component   = VirtualBox, Interface: IVirtualBox, {d1a2295c-d257-4a4c-a9a6-843d87db6f45}
[!] Callee      = IVirtualBox, {d1a2295c-d257-4a4c-a9a6-843d87db6f45}

================================================================

I think it says the machine name i entered isnt exist. But my guest machine's in the VirtualBox is "winXP".


VirtualBox Command Line Management Interface Version 1.4.0
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] FAILED calling aVirtualBox->FindMachine(Bstr(argv[1]), machine.asOutParam()) at line 5707!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070057
[!] Text        = Could not find a registered machine named 'winXP'
[!] Component   = VirtualBox, Interface: IVirtualBox, {d1a2295c-d257-4a4c-a9a6-843d87db6f45}
[!] Callee      = IVirtualBox, {d1a2295c-d257-4a4c-a9a6-843d87db6f45}

I really like to get this thing working. I search on Google n several other places but cant find a proper answer. Pls chk my post n giv me a feed bak.

Cheers 
Milinda

---

### Post by schorsch on 2007-08-20
What is the output of
```
VBoxManage list vms
```

---

### Post by steve.horsley on 2007-08-20
Just to make things clear - it's the name of the VM that you have to specify there, I think - not the Windows machine name that it uses on the network. It's the name that you highlight in the VirtualBox control panel before clicking Start.

If that's the name (winXP) you are using, then sorry, I haven't a clue.

Edit: Good idea, schorsch.

---

### Post by milinda on 2007-08-20
Thanx for helping me.

This was de O/P.

**root@KILLER-M:~#** VBoxManage list vms
VirtualBox Command Line Management Interface Version 1.4.0
(C) 2005-2007 innotek GmbH
All rights reserved.

Pls chk n reply...!

---

### Post by schorsch on 2007-08-20
Hmmm ... actually you do not have any virtual machine defined. Otherwise this command would have given lots of information about your vm(s).

---

### Post by schorsch on 2007-08-20
Ah, I just saw you were root when running this command .... The virtual machines with VirtualBox are per user and not per system. So please login as your user and try this command again .... perhaps you will even be able to add a shared folder with the command you mentioned.
BTW: You should not login as root ...  ;-)

---

### Post by rocksta on 2008-07-09
that completely worked for me. thanks! I also did the mistake of running VBoxManage as root.

---

