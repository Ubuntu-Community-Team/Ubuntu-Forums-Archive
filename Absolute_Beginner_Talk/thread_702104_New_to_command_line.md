---
title: "New to command line"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by dboyd on 2008-02-19
First day of ubuntu server setup. I am able to get to directories where conf files reside. How do I get into edit mode for a config file. for example vsftpd.conf 

Also any help with essential commands for getting started at the command line.

---

### Post by szymon_g on 2008-02-19
for beginners, for viewing config files nano seems to be the best editor. also mcedit is nice (its a part of mc package)
anyway- if you are beginner, maybe installation of gui would be a good choice ?

---

### Post by kristjans on 2008-02-20
[http://mybloges.com/blogs/linux-all/hello-i-am-terminal](http://mybloges.com/blogs/linux-all/hello-i-am-terminal) ;)

---

### Post by aysiu on 2008-02-20
> **dboyd said:**
> How do I get into edit mode for a config file. for example vsftpd.conf Try ```
sudo nano -B vsftpd.conf
``` To save, press Control-X, Y, Enter

---

### Post by dboyd on 2008-02-20
Thanks for showing the usage. I am loving the GUI but forcing myself to using the server. I am aware of the dangers and power of some of the commands. I read the disclaimer on dangerous commands, other newbies reading this post should heed the warnings of others out to have fun at others expense. I wont be delting my files or reformatting unless I intend to. Now I know enough to be dangerous. for know I am learning the ropes and plan to use some of the server products in a practical work application. 

Thanks Again,

DBoyd

---

### Post by szymon_g on 2008-02-20
of course you know that you can use Gui on server machine (at least if your hardware let you to do that ;P)? you dont have to force yourself to doing CLI only job ;)

---

### Post by lnx4me on 2008-02-20
How exactly do you setup samba from the GUI?

---

### Post by dboyd on 2008-02-20
how does one use a GUI on a server machine? All I get after boot up is a command prompt.

---

### Post by aysiu on 2008-02-20
Try [this](http://www.psychocats.net/ubuntu/minimal#barebones).

Skip to the *Enabling Extra Repositories* part.

---

### Post by szymon_g on 2008-02-20
run

startx

if xserver is installed, it will run. if not, you have to install xserver+ desktop environment/window manager.

---

### Post by szymon_g on 2008-02-20
~lnx4me : did i wrot that i setup samba from gui :P? i just tell that some actions (even 'pure' command line) are easier to do when you have Gui running (4 example: its easier to copy/paste some text from one console into another etc). its much easier than alt+F(n) or using screen program.

---

### Post by lnx4me on 2008-02-20
dboyd,
   I commend you on your commitment to learning the CLI. Thats the right attitude to take concerning servers. My previous post was a bit of a jab at GUI's. Not everything is point n click. Samba under ubuntu does not have a point n click way of setting it up.

 So what kind of server are you building?

Oh and BTW vi is the editor I use. well mainly because virtually any nix based system in the world will have it. At first vi may be awkward but once your use to it, it just works.

make a copy of the original file first!

cp vsftpd.conf vsftpd.conf.orig

sudo vi vsftpd.conf  

A very very quick vi tutorial--- Not everything included but enough to get the idea
On my 6.06 LTS server:
use the arrow keys to move around and then press the insert key on the keyboard. look at the bottom left hand corner and it will read Insert. Press the insert key again and it will read Replace meaning replace the text. press the esc key and you can move around with the arrows again. Finally press shft colon and then q enter and your back to the command prompt. If you totally hose up the file then:
 esc shft colon q! enter

---

