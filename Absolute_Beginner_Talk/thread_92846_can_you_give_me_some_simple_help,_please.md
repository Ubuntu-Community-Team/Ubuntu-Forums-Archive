---
title: "can you give me some simple help, please?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-20
hi, i really want to use the internet with Ubuntu but i don't know afew really easy things to configure my modem, like the path to my desktop. i'm following the instructions from [here](http://ubuntuforums.org/showthread.php?t=44763).

first it says do this command:
sudo dpkg -i /path/to/your/download/speedtouch-firmware_0.

i have put the archive on my desktop. can you show me what the command should be, please?

then it says "load the pppoatm module" if i open the terminal and type the following command is that it? - 
sudo modprobe pppoatm
sudo gedit /etc/modules

it then says "in the editor window, add" - "pppoatm" will the "editor window" already be open? or does that mean the terminal

it then just carries on like that. so, if i just open the terminal and copy the commands will it work for me? if it will then all i need to find out is the path to my desktop. thanks.

---

### Post by apjone on 2005-11-20
sudo dpkg -i /home/username/desktop/speedtouch-firmware

---

### Post by Danielle on 2005-11-20
[QUOTE=apjone]sudo dpkg -i /home/username/desktop/speedtouch-firmware[/QUOTE]
thanks, apjone. so if my username is Danielle it would be the command below? thanks again. i hate being a newbie, it's horrible :(
sudo dpkg -i /home/Danielle/desktop/speedtouch-firmware

---

### Post by invalid on 2005-11-20
```
sudo dpkg -i /home/Danielle/Desktop/speedtouch-firmware_0
```

Cheers,
Cb

---

### Post by steve.horsley on 2005-11-20
No. Desktop is spelled with a capital D. 

Also, is "speedtouch-firmware" the real file name?
Also, is your home directory really spelled with a capital D?
If so, then :
**sudo dpkg -i /home/Danielle/Desktop/speedtouch-firmware**

Yes, being a newbie again is uncomfortable. The higher you were with windows, the harder the fall. But it's not as bad as it first looks. Really.

---

### Post by Danielle on 2005-11-20
thank you. i'll go and install and configure my modem now, i hope.

---

### Post by Danielle on 2005-11-20
[QUOTE=steve.horsley]No. Desktop is spelled with a capital D. 

Also, is "speedtouch-firmware" the real file name?
Also, is your home directory really spelled with a capital D?
If so, then :
**sudo dpkg -i /home/Danielle/Desktop/speedtouch-firmware**

Yes, being a newbie again is uncomfortable. The higher you were with windows, the harder the fall. But it's not as bad as it first looks. Really.[/QUOTE]
hi, this is the name of the archive - speedtouch-firmware_0.3012k_all.deb
but, i haven't unpacked it so i suppose what is written is correct ??? with "_0" on the end. Danielle isn't my username but i'll put it as i login. i'll go and try it out. it's quite complicated for my first day with a new OS. i'll be very happy if it all works out. :)

---

### Post by Danielle on 2005-11-20
oh, the file i want to exeucute is called speedtouch-firmware_0. and it's in the .deb archive. will the command below unpack then execute the archive? if Danielle is my username. thanks.

sudo dpkg -i /home/Danielle/Desktop/speedtouch-firmware_0.

---

### Post by steve.horsley on 2005-11-20
You don't have to unpack it. dpkg deals with .deb package files. The command you want is:
sudo dpkg -i /home/Danielle/Desktop/speedtouch-firmware_0.3012k_all.deb

---

### Post by Danielle on 2005-11-20
[QUOTE=steve.horsley]You don't have to unpack it. dpkg deals with .deb package files. The command you want is:
sudo dpkg -i /home/Danielle/Desktop/speedtouch-firmware_0.3012k_all.deb[/QUOTE]
thanks, i've no idea how i got speedtouch-firmware_0. anyway, i realised it was wrong and just tried to get it working. it didn't work :(

when i ran:
sudo modprobe pppoatm
sudo gedit /etc/modulesin

i didn't have:

Code:
noaccomp

and

default-asyncmap

so left that bit out. when i got to the end and ran the last command this is what happens when it tries to connect:

tail -f /var/log/messages

Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readonly:/et c/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readonly:/us r/share/gconf/local.mandatory" to a read-only configuration source at position 1
Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readwrite:/r oot/.gconf" to a writable configuration source at position 2
Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readonly:/et c/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readonly:/us r/share/gconf/local.defaults" to a read-only configuration source at position 4
Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readonly:/us r/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readonly:/us r/share/gconf/debian.defaults" to a read-only configuration source at position 6
Nov 20 22:55:16 localhost gconfd (root-8498): Resolved address "xml:readonly:/va r/lib/gconf/defaults" to a read-only configuration source at position 7
Nov 20 22:55:46 localhost gconfd (root-8498): GConf server is not in use, shutti ng down.
Nov 20 22:55:46 localhost gconfd (root-8498): Exiting

i just noticed that after i got the above i rebooted and when it tried to connected then it wasn't using root, but my username, other bits may have been different too, i'll recheck.

---

