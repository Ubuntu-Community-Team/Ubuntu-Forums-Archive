---
title: "I'm trying to install VirtualBox"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by ettienne on 2007-05-20
I am absolutely new to Linux, I downloaded Ubuntu 7.04 and installed it as the only OS. SO far so good, it is running and I played some games and messed around with Open Office.
My plan is to install VirtualBox and then install Windows XP and Windows Server 2003 and use it for software testing purposes.

I keep hitting a snag with the VirtualBox install, I get an error that I do not have permission to the .deb file - which I downloaded to the desktop.

Does anyone have clear instructions on how to install VirtualBox? I need real idiot proof instructions, I have been using Linux for less than 24 hours.

---

### Post by Kobalt on 2007-05-20
Check [it]("https://help.ubuntu.com/community/VirtualBox") out.

---

### Post by ettienne on 2007-05-20
Thanks, but my problem is with installing VirtualBox, it craps out on the install and I cannot get to run it.

---

### Post by lazyart on 2007-05-20
If you don't have permission to the file, try```
sudo chown -R ettienne:ettienne /home/ettienne/Desktop
``` replacing each reference of ettienne to whatever your actual login name is.

---

### Post by Kobalt on 2007-05-20
When you double-click on the .deb package, the installer should start and at some point ask you for your password. Give it, and then it should go on. Isn't this what's happening when you double-click it ?

---

### Post by ettienne on 2007-05-20
I get the password prompt and enter the password, then after that I get the permissions error.

---

### Post by ettienne on 2007-05-20
Thanks guys, I got it installed.
I installed Automatix ([www.getautomatix.com](www.getautomatix.com)) first, and then used Automatix to install. This is exactly what I was looking for, a one click install, no sudo crap for me.

---

### Post by frodon on 2007-05-21
> **ettienne said:**
> Thanks guys, I got it installed.
I installed Automatix ([www.getautomatix.com](www.getautomatix.com)) first, and then used Automatix to install. This is exactly what I was looking for, a one click install, no sudo crap for me.sudo is for root rigths and automatix use root rights to install things as well.

Installing VirtualBox is not hard at all :

   1. Download the VirtualBox .deb : [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
   2. Double click the deb file
   3. Click the "Install" button
   4. Skip to Configuring 

Here is a full guide about virtual box and ubuntu :
[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by StepanIjin on 2007-07-20
Thanks for Automatix suggestion.
I was screwing around with
1. VMware box (2 days -> find out that the best graphics is 16 colors)
2. VirtualBox using sudo (it gives the agreement, but no 'yes' button. I had to kill the install process, but it suxx, because then I have a broken package with no way to fix it (*)).
3. Qemu which took forever (~15 hours) to get to 'performing final tasks' screen on windows 2k.

Automatix allowed me to install the virtualbox without 'no way to accept virtualbox eula agreement problem'.

Thanks again fot Automatix.


To help people find this topic. Here are the symptoms when I use command line to install.


(*) I ran into a screen 'accept eula'. I can scroll it up and down, but not accept (it is just a text, to prompt, no button). I cancel installation. The installer halted. I killed the process. Attemts to install something else gave 

 
'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.' 

then in the package manager

"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

Tried

sudo dpkg -r VirtualBox 

apt-get -f install

couple other commands that I find on forums. Finally, I reinstalled the Linux.

---

