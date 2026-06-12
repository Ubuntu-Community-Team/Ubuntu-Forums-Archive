---
title: "Howto create a network connection vmware win XP and ubuntu 6.10?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-03-20
Hello, 
is there a guide on how to install the network connection between UBUNTU 6.10 and vmware WIn XP?
Or is there a way to display the win folders and access them under ubuntu?

I want to transferr files between both.

Thanks

---

### Post by cowlip on 2007-03-20
Hi,
you need to share the folders on the network under your virtualized XP install to access them from Ubuntu.  Make sure your computers are in the same workgroup, too.

---

### Post by shareMenaPeace on 2007-03-20
> **cowlip said:**
> Hi,
you need to share the folders on the network under your virtualized XP install to access them from Ubuntu.  Make sure your computers are in the same workgroup, too.

Thank you but do i need to install anything for the network to work?
And where do i set the workgroup in ubuntu?


Thanks (Never done a network before)

---

### Post by hyper_ch on 2007-03-20
did you configure vmware with network capabilities?

You could also setup a samba share on your ubuntu :)

---

### Post by shareMenaPeace on 2007-03-20
I had te default network settings, now i changed to virtuell network. But i dont know how to set this up.

Does someone knows a step by step tutourial/how to?
I just want to transfer a few files.
Currently i have to burn a cd todo this ...

Thanks

---

### Post by lumingzuiku on 2007-03-20
make sure an ethernet card is installed on your vmware XP
choose host-only connection type or bridge if you can get more than one ip.
then use samba to share files

---

### Post by shareMenaPeace on 2007-03-20
Ok i can follow you till --- samba how i use this?

---

### Post by cowlip on 2007-03-20
if you right click on a folder in your xp virtualmachine, you should see a tab that says "sharing".   There's a wizard that pops up too if you haven't shared a folder before that will enable the ports for the firewall, set a workgroup, etc.

Just remember the key thing is for them to be in the same workgroup 

windows control panel->system properties->computer name->ID->"To rename this computer..." click "change" and go to workgroup, and name it 

ubuntu system->administration->networking->workgroup or shared folders , look for workgroup

---

### Post by shareMenaPeace on 2007-03-21
> **cowlip said:**
> if you right click on a folder in your xp virtualmachine, you should see a tab that says "sharing".   There's a wizard that pops up too if you haven't shared a folder before that will enable the ports for the firewall, set a workgroup, etc.

Just remember the key thing is for them to be in the same workgroup 

windows control panel->system properties->computer name->ID->"To rename this computer..." click "change" and go to workgroup, and name it 

ubuntu system->administration->networking->workgroup or shared folders , look for workgroup

Under networking all i have is modem and wireless settings, nothing regarding "workgroup".

I just used synaptic to install samba, but when i try to run "samba" from the terminal nothing happens.
Beside this i have a shared folde and workgroup name assigned under XP.

SO how do i setup samba or how do i start it?

Thanks

---

