---
title: "Installing a driver and other software."
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Mortifer on 2006-12-28
Hi!
I just switched to Ubuntu today, sick of Windows, but I don't really know much about this.
Im trying to install the Intel Wireless Pro 2200BG driver for linux, but don't know how to install such things. Wether through the terminal or GDEBI package installer. That one just gives me errors.

Anyone who can help? :)

---

### Post by Rui Pais on 2006-12-28
Hi, welcome.

You must be more specific.

What are you trying to install? its a deb package? something from a tar? a shell script ?
Where do you get the drivers?
What kind of error? what messages it gives?

---

### Post by deadgobby on 2006-12-28
Your card is supported... That is good. It may take a little work to get it going.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)
Good luck....
;)

---

### Post by Mortifer on 2006-12-28
Yes, sorry. I have read that the kernel I have includes the driver I need for the wireless card, but  need to untar the firmware file into /lib/firmware

I downloaded the firmware which is a .tgz file. I cannot drag the files into the /lib/firmware folder, says I don't have permission. I guess I'm supposed to do this from the terminal?

---

### Post by deadgobby on 2006-12-28
Yes and no. Here is a copy of lonks to book mark too.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
 You can unpack the tar on the desktop with out the terminal. Just right click and scroll down to unpack here. Once unpacked, read the Install File on the new folder. It could be simple as clicking.
Gobby

---

### Post by Rui Pais on 2006-12-28
> **Mortifer said:**
> 
I downloaded the firmware which is a .tgz file. I cannot drag the files into the /lib/firmware folder, says I don't have permission. I guess I'm supposed to do this from the terminal?

You tried to move files to a place of the system where, as a normal user, you don't have permissions to write.
The best way to move it is from a terminal:
```
sudo mv <files> /lib/firmware/
```
it will ask for password and after that will copy.

---

### Post by Mortifer on 2006-12-28
I think I might have figured out the problem. It seems all the driver and firmware files I download are already in the filesystem, but my wireless card is not turned on. I used to do that through hotkeys on the side of the keyboard by installing a launch manager. Anyone experienced this? Any way to replace that key or install a similar software on linux?

---

### Post by riven0 on 2006-12-28
> **Mortifer said:**
> I think I might have figured out the problem. It seems all the driver and firmware files I download are already in the filesystem, but my wireless card is not turned on. I used to do that through hotkeys on the side of the keyboard by installing a launch manager. Anyone experienced this? Any way to replace that key or install a similar software on linux?

Try this in the terminal first:
> 
iwconfig

If that doesn't work, post the output of this command:

> sudo /etc/network/interfaces restart

And this one, too:

> cat /etc/network/interfaces

---

