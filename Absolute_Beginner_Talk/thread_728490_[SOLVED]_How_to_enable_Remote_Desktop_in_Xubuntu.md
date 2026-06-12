---
title: "[SOLVED] How to enable Remote Desktop in Xubuntu"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-18
Trying to find info on enabling Remote Desktop in Xubuntu.

This entails turning on:
1)  Allow other users to view your desktop
2)  Allow other users to control your desktop
3)  Require the user to enter this password

This is in preperation for ssh and tunneling in Putty or even TightVNC.

Any help to understand how to do this in Xubuntu, whether in the GUI or command line, would be greatly appreciated!

---

### Post by Hospadar on 2008-03-18
well if you want ssh, which is by far the most secure option, the quickest way to get that happening is to go to a terminal and ```
sudo apt-get install ssh
```  This will allow remote users to login with something like "ssh <local username>@<your ip address>" if you do a "man ssh" there are some command line arguments (-Y) that will let you tunnel X connections to open up graphical apps if your remote client is running an xserver (aka using linux, or running something like xming on windows)

ssh will give you command-line control, and the ability to open up graphical applications from the command line.  It's also by far the most stable and secure remote system.  Also ssh will allow for file transfers with scp, or a program like filezilla or gftp (using sftp protocol)

If you want a total remote desktop, you can use vnc.  I forget where in the xubuntu menu this is, but if you Alt-F2, and run "vino-preferences" you can get the dialog to enable vnc connections.

Note that if you are behind a router and you want to connect to the machine from outside the router, you will need to foreward ports on the router to the host machine, port 22 for ssh, and port 5 thousand something (I forget the exact port, but I'm sure someone here knows it) for vnc.

Also note, with ssh there really isn't an easy way to open up a graphical application, start it doing something, and close your ssh connection and have the app still run.  I think it is technically possible to move it to the main X server, but I've tried and it's not easy.  For command line apps, you can use "nohup" so they continue to run after you log out.  So if you need to maintain graphical apps from a distance, vnc might be a better choice.

Hope this helps!

---

### Post by BlizzofOZ on 2008-03-18
While I have successfully remote connected using Putty, with tunneling, I can't seem to get RealVNC to work.

Thank you very much as the Alt-F2 vino-preferences brought the dialog that I was looking for.

Yet, with the features turned on, I cannot get RealVNC to connect.

I get the following error:
failed to connect: Connection refused (10061)

Any help?

---

### Post by BlizzofOZ on 2008-03-19
Has anybody encounter this problem before?

Any help would be appreciated!

---

### Post by PhrankDaChickenGeek on 2008-03-26
the vino server needs to be started - see:

[http://ubuntuforums.org/showthread.php?p=4531102#poststop](http://ubuntuforums.org/showthread.php?p=4531102#poststop)

---

### Post by saj0577 on 2008-03-26
Maybe a networking error?

Saj

---

### Post by deadowl on 2008-03-31
Any word if this is going to be fixed in Hardy?

---

