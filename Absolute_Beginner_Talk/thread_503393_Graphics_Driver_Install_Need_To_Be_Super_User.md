---
title: "Graphics Driver Install Need To Be Super User??"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by sunami900 on 2007-07-17
now it says i need to install it as the 'super user'
uh how to i fix it or become super user

---

### Post by wormser on 2007-07-17
If you are installing via the command line just add **sudo** infront of your command.  Then use your password.  Give us more details.

---

### Post by sunami900 on 2007-07-17
Still Doesn't Work---
Yeah stills says I need to be logged in as the super user.:mad:

---

### Post by vonfeldt7 on 2007-07-17
try entering "gksudo" before it, instead of just "sudo"

---

### Post by aktiwers on 2007-07-17
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mustafayatagan on 2008-01-02
The same thing i've seen. I solve this by this way after long long search:

Start ubuntu regularly with GUI.
Open terminal window
type "su" and enter
when prompted type your /root password.
then you have a session with super-user priviligies
by using bash commands, navigate to where ".run" package is.
then type
sh <application.run>
<application.run> is the name of the package you want to install.

Linux will extract the package and begin to install.
After all, restart the system.

Note: The super-user session is only available for the terminal application window. If you close the terminal window and reopen, you will have to use "su" command again.

Another Note: I'm newbee on linux. I could have some mistakes. if so i appologize for this. I like linux, and i lke Ubuntu.

---

