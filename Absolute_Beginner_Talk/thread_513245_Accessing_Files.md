---
title: "Accessing Files"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by homesy on 2007-07-30
Well im new to this ubuntu only had it 3 days but ive managed to get things so far without requesting too much help.

to give you a bigger picture this is what im using :

Server (ubuntu)
Gaming PC (windows XP Pro)
Normal PC (vista ultimate) - Non Important
Laptop #1 (SUSE Linux) - Non Important
Laptop #2 (windows XP Pro) - Non Important

So far ive managed to setup Samba and i can now access and see my C:/ and D:/ drives on my Ubuntu Server from my gaming PC , i can access these drives no problem (havnt tried altering these files - so i dont know if its just set to read only or read and write). I have KNetwork Manager , But dont really know if i need it of what im doing with it :) .

what i would like to be able to do now, is to be able to see my File System (ubuntu) on my gaming pc. all computers are setup on the network and working fine. i would just like to be able to set it so i can read and write to all the drives on the server and gaming PC and set up the file system to be shared across the whole network so all computers can read without permission , and write to it with permission. :confused:

help with this would be appriciated greatly. 
Thanks.

---

### Post by AtrejuT on 2007-07-30
You could have a look at this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

the guide is for edgy but I presume it works the same way in feisty.
hope this helps

---

### Post by bodhi.zazen on 2007-07-30
You *could* mount the Ubuntu server root directory / via samba or NFS, but why ? Most system files do not need such access. Perhaps mount /home as a shared directory or a shared /data partition.

You can manage the server via ssh or vnc or webmin.

---

