---
title: "DVD authoring"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-10-27
Hi what is the best Video authoring software for Ubuntu ?? actually using Kubuntu if that makes any difference ???  on Windows i use ULead - but my windows drive is terminally sick - so i want to see whats on offer here ??? all i really need is to capture video from a DV camcorder (cannon) and edit then burn to cd .... also whils here where/ how do i download the mp3 drivers ?

---

### Post by swisscow on 2007-10-27
Kino is one for downloading the dvd stuff

Mp3 drivers - add the ubuntu restricted extras from add remove  (I think that's right but someone will correct me if I'm wrong) - which will add lots of codecs to your system

---

### Post by lupgop on 2007-10-27
I have downloaded Kino - it doesnt seem to see my camera - i looked in help but it a bit over my head ...  went into preferenecs as i gather i should have raw1394 ? under the IEEE 1394 tab it says - 
The IEEE 1394 Subsystem is not responding. 
The raw1394 module must be loaded, and uou must have read and write access to /dev/raw1394

i am logged in with the only password and under permissions on the file /dev/raw1394 it says owner and group have read/write others are forbiden ??? (tried letting others have read write too , but it said access denied to /dev/raw1394 ??????????

so i guess what im asking is a/ how do i load the raw1394 module and b/ do i have acces ???

---

### Post by schristo on 2007-10-29
I believe that the raw1394 node belongs to the disk group. This means you should add your main user to that group (through administration->Users and groups). Another, non-permanent and not so safe solution is to give everyone read/write access to raw1394. This can be done through the command

sudo chmod 0666 /dev/raw1394. 

If you do that and reload Kino, you will have full access to your videocamera controls.

---

