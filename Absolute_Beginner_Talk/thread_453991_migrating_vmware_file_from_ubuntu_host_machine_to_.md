---
title: "migrating vmware file from ubuntu host machine to windows host machine"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by paxmanchris on 2007-05-25
ok. 
i am running vmware server on ubuntu gnome desktop.
i have ubuntu-server installed to a vmware virtual disk. 
i have another computer (windows), which i installed vmware player. 
according to everything i read, i should be able to copy the file and run in on the vmware player on my windows computer.
BUT
for some reason the network does not work.

i do a ifconfig command and only the loop back device comes up.

i really need some guidance on this.

please help me

---

### Post by eentonig on 2007-05-25
Probably the VMWare network devices aren't setup the same way as you had them on your linux box. So this is more a VMWare support question.

Can you verify in VMWare what you're available network interfaces are? Bridged, NAT, private-only?

---

### Post by paxmanchris on 2007-05-25
i have the options for bridged nat and private. i tryed them all.

is there any command to reconfigure the network card?

---

### Post by paxmanchris on 2007-05-25
**PROBLEM SOLVED!!!!!!!!!!!!**

all i had to do was delete: **/etc/iftab**

i am so happy i_[ found the slution.]("http://www.vmware.com/community/thread.jspa?messageID=587106&#587106")_ i had to scoure the internet for a strait foward answer.

---

