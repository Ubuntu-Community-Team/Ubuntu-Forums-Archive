---
title: "Auto-login as root"
date: 2011-12-09
forum: Any Other OS
---

### Post by AlvitrValkyrie on 2011-12-09
Hey. I'm wondering how to make Mint auto-login as root. Or prompt for the root user and pass, then to start the x windows system, like Backtrack 5 does (preferable, but can be in the tty1 screen with the default kernel).  I do a lot on my system (Mint 12) that requires root privilege, and I understand the risks of running as root. Having to type in the password again and again gets annoying.
Thanks for all your help in advance!

---

### Post by raja.genupula on 2011-12-09
Hi man 
You can disable your prompt for password prompt while moving as a root and you told us that no problem with the risks ,

look at here
 [https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo](https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo)

I am sure that gonna help you.

---

### Post by Synoc on 2011-12-09
do you plan on doing all your administration from the GUI?

if you don't need a GUI, I recommend doing a ```
 sudo bash 
``` then yol only need to close your xterm window and you are back to secure. 

if you NEED a GUI... do as you will

---

### Post by Perfect Storm on 2011-12-09
Moved to Other OS/Distro Talk.

---

### Post by AlvitrValkyrie on 2011-12-09
> **raja.genupula said:**
> Hi man 
You can disable your prompt for password prompt while moving as a root and you told us that no problem with the risks ,

look at here
 [https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo](https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo)

I am sure that gonna help you.

Thanks, man. I'll check it out later.

---

