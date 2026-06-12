---
title: "Screen resolution need help"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Brudy on 2007-05-01
I have tried the sudo dpkg-reconfigure xserver-org, and cannot get passed the login after the command in termibal mode, the key pad is not recognised for input of the password.
I have tried the screen resolution in the screen reolution, and I have only the 640 x 480, and I can do nothing with it.
I have read other post's but I don't think I understand enough about this OS to make it.

Help
E-mail would be good to
[email]Roodvoets@charter.net[/email]

---

### Post by bobplano on 2007-05-01
then you can always manually edit the xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
then add resolutions if they aren't there, or change which drivers your using. what do you mean the keypad is not a valid way to enter your password?

---

### Post by Brudy on 2007-05-01
> **bobplano said:**
> then you can always manually edit the xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
then add resolutions if they aren't there, or change which drivers your using. what do you mean the keypad is not a valid way to enter your password?

the key board will not type when I have entered the sudo command, and then it asks for my password, but will not let me type it, or cut and past it.

---

### Post by Brudy on 2007-05-01
I have tried your manual sudo command, and as soon as I type in the sudo command the system askes for my password, but will not let me type it.

---

### Post by Gazneth on 2007-05-01
The password prompt does not echo password input for security reasons, try it again then press enter.

---

### Post by Gazneth on 2007-05-01
Here is a how to I like to use when running ```
sudo dpkg-reconfigure xserver-xorg
```
It seems to work better for me when you boot into the recovery console, text mode terminal only. Then type command and follow how to.  Good luck.[HTML]http://users.bigpond.net.au/hermanzone/p7.html[/HTML]

---

### Post by Brudy on 2007-05-01
bryan@bryan-desktop:~$ sudo dpkg-reconfigure xserver-org
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed
bryan@bryan-desktop:~$

Here is the reply I recieved in terminal mode.
I am sure that I'm doing somthing wrong 
thanks for the tip on the pass word.

---

### Post by Gazneth on 2007-05-01
actually you are just mis spelling the command, the end of the command is: xserver-xorg,  not org.

---

### Post by Brudy on 2007-05-01
Thanks
I made it into the xserver, and now I can read your reply w/o having to scrowl over, I'm not out of the woods yet but thank you
Sincerely
Brudy

---

### Post by Gazneth on 2007-05-01
:biggrin:  read the how to I posted above there is even a link in that one to another one written by one of the forum mods. They should help you get your xserver set up perfect.

---

### Post by Brudy on 2007-05-01
I have the link up on the computer to my left, I'm looking to get away from windows, I have lots of $ tied up into programs that are usless under vista. also what started this adventure is the CNC / EMC2 portion of this program.
Thank You

---

### Post by Brudy on 2007-05-01
I just pulled up the link using this computer runnung ubuntu, and the page is larger than the screen again.

---

