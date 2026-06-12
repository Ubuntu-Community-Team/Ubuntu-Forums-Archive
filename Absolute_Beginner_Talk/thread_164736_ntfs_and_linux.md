---
title: "ntfs and linux"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by 08bell20 on 2006-04-23
Is there any way of getting an external ntfs hdd to work on linux without having to format it to FAT...etc or whatever it is? i can read but not write...pretty much what i expected.
 i also cannot read my ubuntu partition, "i do not have the permissions necessary to view the contents of "hda1". 

Any help?

cheers

---

### Post by benvdh on 2006-04-23
Hey,

fort the external hdd, it's not directly possible to write to an ntfs partition since ntfs write support is only available in some of the newer kernels. What you could try is installing the following project :
[URL="http://www.jankratochvil.net/project/captive/"]
http://www.jankratochvil.net/project/captive/[/URL]

Use the following how-to, to install:

[http://www.ubuntuforums.org/showthread.php?t=10175]("http://www.ubuntuforums.org/showthread.php?t=10175")

For an answer to your second question you will have to be a bit more specific. From where are you trying to read your ubuntu partition ?
Access to which part of the partition ?

Regards,

Ben

---

### Post by 08bell20 on 2006-04-23
well i created a partition on my internal hd for linux, but now when i try to read it from the icon on the desktop i cant, but i can read it on the disks manager

---

### Post by benvdh on 2006-04-23
You could try having a look at your /etc/fstab file. To do this, open a terminal and type the following command :

> less /etc/fstab 
Have a look at the line of the partition you're having difficulties with.
if the line doesn't have an option (part of the line where things a comma seperated) like user or users then that is probably the problem. To solve this problem, open the file using an editor:

> sudo gedit /etc/fstab 
and add the following option behind the last option (comma seperated value)

For example, if this is your line:

> /dev/hdb2 /media/hdb2 reiserfs defaults,atime,auto,rw,dev,exec,suid,nouser 0 2 
add this option : uid={username}

( where you replace {username} with the user that needs access to the partition. so for me it would be uid=ben )

like this:

> /dev/hdb2 /media/hdb2 reiserfs defaults,atime,auto,rw,dev,exec,suid,nouser,uid=ben 0 2 
When you've finished editing the file, save it and reboot.

Regards,

Ben

ps. if you do have the user or users option and it still doesn't work, also try the above. Also make no mistakes when editing this file, it could have major consequences.

---

