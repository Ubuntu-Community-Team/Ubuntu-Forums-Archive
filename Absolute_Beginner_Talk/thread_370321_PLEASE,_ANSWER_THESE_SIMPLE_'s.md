---
title: "PLEASE, ANSWER THESE SIMPLE ?'s"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by kcim_strebor on 2007-02-25
PLease, I am new to Ubuntu and would like to know how to open a window to put in a command line, then how to change the computer name. Also, is it possible to shre a printer with a windows xp system?

---

### Post by s_x_g_t on 2007-02-25
you put your commands in the progam called TERMINAL  it should be under applications. To change your user name go to users and groups under Admin

---

### Post by moore.bryan on 2007-02-25
[I]if your using gnome, it's the terminal in programs (at least, that's what i think it's called).  what do you mean by "change the computer name?"  and yes and there are plenty of posts around the forums about how to do it.
:-)
[/I]

---

### Post by paydaydaddy on 2007-02-25
open a terminal for entering a command line by clicking <applications><accessories><terminal>

Lots of good info at the following page:

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

It is possible to share a printer with an XP system. I do it. How it is done depends on your setup. Whenever you ask for help please help those who would help you by providing important info such as which distrabution you are using, kind of printer, type of connection, etc. Be sure to search the forums for answers. I don't know how to change the computer name, but I'll bet it's not difficult. While you're waiting for somebody to jump in with the answer, try doing a search on the subject. Good Luck.

---

### Post by kcim_strebor on 2007-02-25
Thanks to you all, that all really helped! Now, when I am in terminal and I input commands I get the error message "permission denied." Any ideas? Here is my info:

I am running Edubuntu 6.06 LTS on an IBM ThinkPad 600E with a Pentium II processor ans 128MB of RAM.

The printer I have on the network is an Epson Stylus Photo R300. I currently share it only with other windows based machines wirelessly over an infrastructure network.

---

### Post by george29 on 2007-02-25
you probably need root permission - type 'sudo' in front of the command you are trying to use and type your password when asked...

---

### Post by Maestro23 on 2007-02-25
> **george29 said:**
> you probably need root permission - type 'sudo' in front of the command you are trying to use and type your password when asked...

Just want to add: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jkeyes0 on 2007-02-25
> **kcim_strebor said:**
> PLease, I am new to Ubuntu and would like to know how to open a window to put in a command line, then how to change the computer name. Also,** is it possible to shre a printer with a windows xp system?**

Yes, it is possible to share a printer with an XP system. If you click
System ==> Administration ==> Printing, 
then in the new window, click "New Printer", it will provide you with a wizard to set up the printer. If your XP machine is sharing the printer, you will need to choose "Network Printer", and change the type from "CUPS Printer" to "Windows Printer", and provide all the necessary details on the printer. Note: you might have to use the IP address of your windows machine instead of its name, since by default WINS resolution does not work in Ubuntu.

---

### Post by steve.horsley on 2007-02-25
When you change the computer name, you must make sure that both these files:
    /etc/hosts
    /etc/hostname
are changed at the same time. You can do this from the command line, but until both files match again, sudo will be broken, so you should do it from a root prompt (sudo su) rather than using sudo to launch the editor.

You would be much safer using the GUI - System->Administration->Networking and change the host name under the General tab there - it will change both files simultaneously.

---

