---
title: "Saving system config"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by quirkydreamer on 2007-03-14
Hi,

I want to use Ubuntu as a stand alone system for storage that will run from CD. Yet, i would like to config the system (IP address, DNS etc) and save it either to FDD or USB memory. So if i have to reboot i can load in my configuration file.

Is this possible? If so, which application do i need to use?

Thank you for time in this matter,

Rowland

---

### Post by mac.ryan on 2007-03-14
If I understood what you want to achieve, then it would be enough to backup the directories containing your configuration files (stored in the direcotry /home/*usernamehere*). All configuration data - AFAIK - are stored in hidden files and directories (eg: /home/*usernamehere*/.gnome).

I personally use "Simple Backup Config" and "Simple Backup Restore" applications to managed my backups. They are of course "Simple" and they just work! :)

[Certain configuration data are owned by the *root* user... the backup can save those too, but they are saved in other directories than /home/*usernamehere*]

Hope I didn't misunderstand your question...

---

### Post by tagra123 on 2007-03-14
What you're asking for  is called live cd persistence.

See my post.
[http://ubuntuforums.org/showthread.php?t=372193](http://ubuntuforums.org/showthread.php?t=372193)

I used a small partition on the harddrive, but a flash or usb stick or drive should work too. 

You can even install programs and they will be there when you boot up.


The one I have set up on a memory stick has two different Xorg.conf files.  One is called xorg.conf.ati and the other is call xorg.conf.nvidia.  When I boot up on the same machine I used last time I do nothing. When I go to a different machine I just go to the terminal and type 

```
cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf 
``` 

for the machine with the nvidia card  same command for the ati card but substitute ati for nvidia.   

It would be real nice if I could figure out how to detect automatically but I can take a working desktop with my favorite programs to almost any machine this way.

---

### Post by mac.ryan on 2007-03-15
> **mac.ryan said:**
> If I understood what you want to achieve

Sorry... evidently I did not! :(

---

### Post by GadeTerbob on 2007-03-16
I've just found directions for Dapper here:

[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

However, can someone point me to directions for Edgy?
Or tell me that there is no difference??

TIA

PS: It's this community that will make Ubuntu great!!

---

### Post by tagra123 on 2007-03-17
The dapper how to works in Edgy.  See my post above. I used it with no problems.

---

